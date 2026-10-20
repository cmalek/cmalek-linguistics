---
title: >-
  Split a large Python module into a package
category: skills
tags: [python, refactoring, ruff, mypy]
relationships:
  - target: "[[skills/claude-code-builtin-cd]]"
    type: related_to
  - target: "[[skills/verify-plan-in-throwaway-worktree]]"
    type: related_to
  - target: "[[skills/rebase-diverged-refactor]]"
    type: related_to
sources:
  - "agent:access.caltech-proxy-session-2026-10-13"
summary: >-
  Gotchas from slicing a 2,400-line module into a package: ruff prunes imports before use, Protocol params, __all__ narrowing star-imports, patch targets, and shell quirks.
provenance:
  extracted: 0.9
  inferred: 0.1
  ambiguous: 0.0
base_confidence: 0.55
lifecycle: draft
lifecycle_changed: "2026-10-15"
tier: supporting
created: 2026-10-15T00:00:00Z
updated: 2026-10-15T00:00:00Z
snapshots:
  - "[[_raw/_archived/2026-10-13-python-module-to-package-split-gotchas|2026-10-13-python-module-to-package-split-gotchas]]"
---

# Split a large Python module into a package

A 2,398-line `cache.py` was split into a `cache/` package by line-range slicing, with a re-exporting `__init__`. The suite stayed green (696 passed) once the five problems below were fixed.

## Order of operations for ruff

```mermaid
flowchart LR
    A[Slice module by line range] --> B[Edit code: new aliases, new param types]
    B --> C[Add imports]
    C --> D["ruff check --select F,I --fix (last)"]
    D --> E[mypy + tests]
```

Add imports before the code that uses them and `ruff --select F401 --fix` deletes them as unused, which later shows up as F821 undefined names. Make the code edits first, add imports second, run `ruff check --select F,I --fix` last. Confirmed: the F821 errors went away after reordering.

## Protocol parameters must match implementations

mypy rejected `dict[str, ApplicationIndex]` entries for classes that structurally satisfied a `Protocol`. The protocol declared `load(self, apps: Sequence[X])` while implementations took `list[X]`; parameters are contravariant, so the narrower implementation parameter is incompatible. Declare the protocol parameter as the narrowest type the implementations accept. Inside a class that defines a method named `list`, annotate with `builtins.list[...]`, or the name resolves to the method in class scope.

## `__all__` narrows a star-import

`models/__init__.py` did `from .cache import *`, and the old module had no `__all__`, so every public name, including `logger` and `Settings`, was re-exported. Adding an explicit `__all__` to the package shrinks that surface. Tests that did `mocker.patch.object(cache_mod.logger, ...)` then failed with `AttributeError`.

- Patch the real owner (`from acproxy.logging import logger`, `import bonsai`) or the specific submodule (`cache.reload.create_task`).
- A patch on a name looked up in a module (like `create_task`) has to target the module where the code under test does the lookup.

## Break a circular import with an injected callback

A lazy `from acproxy.app.tasks import Status` inside a reload method existed only because `tasks` imports `models`. Replace it with an optional coroutine callback (`on_reloaded`) passed in from the composition root (`main.py`: `on_reloaded=Status().write`). Tests that patched the lazily imported class now pass the callback, and assertions on `register_watchdog(app, wd)` must expect the extra argument.

## Environment quirks

- Compound `cd <path> && cmd` sometimes failed with `chdir: command not found` and the `cd` silently did not happen. Use absolute paths and `git -C`. See [[skills/claude-code-builtin-cd]].
- `git stash` leaves untracked files behind, so a "baseline" mypy or ruff run after stashing a refactor that added a new untracked package is not a real baseline. Write `git show HEAD:<file>` to a temp file and compare against that. See [[skills/verify-plan-in-throwaway-worktree]] for a cleaner alternative.
- `.venv/bin/mypy` can fail with `Invalid python executable ... pyenv shims`; pass `--python-executable .venv/bin/python`.

## Sources

- [[_raw/_archived/2026-10-13-python-module-to-package-split-gotchas]]
