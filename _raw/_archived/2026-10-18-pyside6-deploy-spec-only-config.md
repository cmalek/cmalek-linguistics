---
title: "pyside6-deploy pyproject.toml support needs a newer PySide6 than 6.11.2"
category: skills
tags:
  - topic/pyside6
  - topic/packaging
  - topic/nuitka
summary: "PySide6 6.11.2 pyside6-deploy ignores pyproject.toml; current docs describe [tool.pyside6.deploy] (6.12.0 assumed). Moved venv leaves stale shebangs."
tier: supporting
related: []
extends: null
contradicts: null
superseded_by: null
capture_source: claude-session
project: "aenglisc_toolkit"
base_confidence: 0.75
lifecycle: draft
lifecycle_changed: 2026-10-18
provenance:
  extracted: 0.75
  inferred: 0.25
sources:
  - "aenglisc_toolkit session (2026-10-18)"
---

## [tool.pyside6.deploy] is documented but absent from 6.11.2

CORRECTION: an earlier draft said pyproject.toml is unsupported. The current Qt docs describe a `[tool.pyside6.deploy]` table. Supported keys: title, input_file, exec_directory, icon, mode, extra_args, macos_permissions. Precedence: CLI > pyproject > spec. `pyside6-deploy --init` merges it into the generated spec. Machine-derived fields (modules, plugins, packages) stay in the spec. Installed 6.11.2 has no such code; PyPI latest is 6.12.0, assumed but not verified to have it. ^[inferred]

Original observation for 6.11.2:

**Behavior:** In PySide6 6.11.2, `pyside6-deploy` takes its settings from an INI file, `pysidedeploy.spec`, which it generates and updates itself. Settings such as `mode` (default `onefile`) and `extra_args` live there. The `pyproject` references in `PySide6/scripts/deploy_lib/config.py` are `pyside6-project` file lookups, not deploy settings.

**Explanation:** The tool wraps Nuitka and compiles to native code. It is not a bundler like PyInstaller.

**Workaround / Pattern:** To keep settings in `pyproject.toml`, write a small build script. It reads a `[tool.<name>.deploy]` table, renders a throwaway spec into a gitignored `build/` directory, runs `pyside6-deploy -c <spec>`, and deletes the spec. The alternative is to call Nuitka directly with the same table. ^[inferred]

**Confirmed by:** Reading the installed package source (`deploy_lib/config.py`, `default.spec`). `pyside6-deploy` itself was never run. ^[inferred]

## Moved venv leaves stale script shebangs

**Problem:** `.venv/bin/pyside6-deploy` failed with "bad interpreter", pointing at `/Users/cmalek/src/workspace/aenglisc_toolkit/.venv/bin/python`.

**Root cause:** The venv was created under a different path (`workspace/`) and the project was later moved. Console-script shebangs hard-code the original venv path.

**Fix:** Rebuild the venv (`uv sync` after removing `.venv`). Not yet applied.

**Notes:** The project's `.venv/bin/python` itself runs and reports Python 3.14 with PySide6 6.11.2. Check that Nuitka supports 3.14 before committing to `pyside6-deploy`. ^[ambiguous]
