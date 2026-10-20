---
title: >-
  pyside6-deploy on PySide6 6.11.2
category: skills
tags: [pyside6, packaging, nuitka, aenglisc-toolkit]
relationships:
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-os-integration]]"
    type: related_to
  - target: "[[references/qt-official-docs-best-practice]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/aenglisc-toolkit]]"
    type: related_to
sources:
  - "agent:aenglisc-toolkit-session-2026-10-18"
summary: >-
  On PySide6 6.11.2, pyside6-deploy reads pysidedeploy.spec, not the documented pyproject table. A moved venv also leaves a stale script shebang.
provenance:
  extracted: 0.70
  inferred: 0.20
  ambiguous: 0.10
base_confidence: 0.42
lifecycle: draft
lifecycle_changed: "2026-10-20"
tier: supporting
created: 2026-10-20T15:55:46Z
updated: 2026-10-20T15:55:46Z
snapshots:
  - "[[_raw/_archived/2026-10-18-pyside6-deploy-spec-only-config|2026-10-18-pyside6-deploy-spec-only-config]]"
---

# pyside6-deploy on PySide6 6.11.2

[[projects/aenglisc-toolkit/aenglisc-toolkit|aenglisc_toolkit]] is moving to `pyside6-deploy` ([[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-os-integration]]). The Qt for Python docs describe a `[tool.pyside6.deploy]` table. The 6.11.2 install that was read does not.

## What 6.11.2 actually reads

`pyside6-deploy` takes an INI file, `pysidedeploy.spec`, which it writes and updates. `mode` defaults to `onefile`. `extra_args` lives there too. The tool wraps Nuitka and compiles to native code. It is not a bundler in the PyInstaller sense.

In `PySide6/scripts/deploy_lib/config.py`, the `pyproject` mentions are lookups for `pyside6-project`, not deploy settings. This was read from the installed package (`config.py` and `default.spec`). `pyside6-deploy` itself was not run. ^[inferred]

## What the current docs describe

The docs' `[tool.pyside6.deploy]` keys are `title`, `input_file`, `exec_directory`, `icon`, `mode`, `extra_args`, and `macos_permissions`. Precedence is CLI, then pyproject, then spec. `pyside6-deploy --init` merges the table into the generated spec. Fields the machine derives (modules, plugins, packages) stay in the spec. An earlier note in the same draft had said pyproject was unsupported; that was the 6.11.2 behaviour, not the current doc. PyPI's latest at the time of the note was 6.12.0. That 6.12.0 contains this table was assumed from the docs, not checked by installing it. ^[inferred]

Until the project is on a release that implements the table, a small build script can read a private `[tool.<name>.deploy]` table, write a throwaway spec under a gitignored `build/`, run `pyside6-deploy -c` on it, and delete the spec. Calling Nuitka with the same table is the other route. ^[inferred]

## Moved virtualenv

`.venv/bin/pyside6-deploy` failed with "bad interpreter". The venv had been created when the project lived under a `workspace/` checkout and was not recreated after the move, so the console-script shebang still names that old Python. The venv's `python` itself ran and reported Python 3.14 with PySide6 6.11.2. The fix is to remove `.venv` and `uv sync`. That had not been done when the note was written. Whether Nuitka supports 3.14 is still open. ^[ambiguous]

## Open Questions

- Does PySide6 6.12.0 actually ship `[tool.pyside6.deploy]`?
- Does Nuitka support the project's Python 3.14?

## Sources

- [[_raw/_archived/2026-10-18-pyside6-deploy-spec-only-config.md]]
