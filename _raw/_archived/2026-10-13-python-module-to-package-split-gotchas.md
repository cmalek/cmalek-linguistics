---
title: "Splitting a large Python module into a package: tooling gotchas"
category: skills
tags:
  - topic/python
  - refactoring
  - ruff
  - mypy
summary: "Gotchas hit splitting a 2,400-line module into a package: ruff --fix prunes imports before use, Protocol vs list params, star-import surface, patch targets, shell/git quirks."
tier: supporting
related: []
extends: null
contradicts: null
superseded_by: null
capture_source: claude-session
project: "access.caltech-proxy"
base_confidence: 0.85
lifecycle: draft
lifecycle_changed: 2026-10-13
provenance:
  extracted: 0.9
  inferred: 0.1
sources:
  - "access.caltech-proxy session (2026-10-13)"
---

# Splitting a large Python module into a package: tooling gotchas

Findings from splitting `acproxy/app/models/cache.py` (2,398 lines) into a `cache/` package by line-range slicing, with a re-exporting `__init__`. Suite stayed green (696 passed) after the fixes below.

## ruff --fix removes imports you are about to use

**Problem:** After generating each new module with a full import header and running `ruff check --select F401 --fix`, imports I intended to use in a *later* edit (a new type alias, a new parameter type) were already pruned, producing F821 undefined-name errors.

**Root cause:** F401 fixes run against the current text; imports added ahead of the code that uses them count as unused.

**Pattern:** Make the code edits first, then add imports, then run `ruff check --select F,I --fix` last.

**Confirmed by:** F821 errors disappeared after reordering.

## Protocol method params must match concrete signatures exactly

**Problem:** mypy rejected `dict[str, ApplicationIndex]` entries (dict-item errors) for classes that structurally satisfied a `Protocol`.

**Root cause:** The protocol declared `load(self, apps: Sequence[X])` but implementations took `list[X]`. Parameters are contravariant, so a narrower impl param is incompatible.

**Fix:** Declare the protocol param as the narrowest type the impls accept. Inside a class that defines a method named `list`, annotate with `builtins.list[...]`, otherwise the name resolves to the method in class scope.

**Confirmed by:** mypy clean on the package.

## Star-import surface changes when you add `__all__`

**Behavior:** `models/__init__.py` did `from .cache import *` and the old module had no `__all__`, so every public module-level name (including `logger`, `Settings`) was exported. A package `__init__` with an explicit `__all__` narrows this. Tests that did `mocker.patch.object(cache_mod.logger, ...)` or `cache_mod.bonsai` broke with AttributeError.

**Pattern:** Patch the real owner (`from acproxy.logging import logger`, `import bonsai`) or the specific submodule (`cache.reload.create_task`). Patches on a *name looked up in a module* (e.g. `create_task`) must target the module where the code under test looks it up.

## Breaking a circular import with a callback

**Pattern:** A lazy `from acproxy.app.tasks import Status` inside a reload method existed only because `tasks` imports `models`. Replace with an injected optional coroutine callback (`on_reloaded`) passed from the composition root (`main.py`: `on_reloaded=Status().write`). Existing tests that patched the lazily imported class must instead pass the callback, and tests asserting `register_watchdog(app, wd)` must now expect the extra argument.

## Environment quirks

- In this Claude Code shell, compound `cd <path> && cmd` sometimes failed with `chdir: command not found` (shell snapshot/hook interference); the cd silently did not happen. Use absolute paths and `git -C`.
- `git stash` does not stash untracked files, so a "baseline" mypy/ruff run after stashing a refactor that added a new untracked package is not a real baseline. Compare against `git show HEAD:<file>` written to a temp file instead.
- `.venv/bin/mypy` may fail with "Invalid python executable ... pyenv shims"; pass `--python-executable .venv/bin/python`.
