---
title: >-
  pytest-qt offscreen on macOS
category: skills
tags: [pyside6, testing, qt, aenglisc-toolkit]
relationships:
  - target: "[[references/qt-official-docs-best-practice]]"
    type: contradicts
  - target: "[[synthesis/Research: Qt and Translation Workbench Best Practice]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/aenglisc-toolkit]]"
    type: related_to
sources:
  - "agent:aenglisc-toolkit-session-2026-10-18"
summary: >-
  aenglisc_toolkit pytest-qt runs on macOS with QT_QPA_PLATFORM=offscreen and no DISPLAY. Qt Test's "only on X11" line is not an install requirement there.
provenance:
  extracted: 0.70
  inferred: 0.25
  ambiguous: 0.05
base_confidence: 0.42
lifecycle: draft
lifecycle_changed: "2026-10-20"
tier: supporting
created: 2026-10-20T15:55:46Z
updated: 2026-10-20T15:55:46Z
snapshots:
  - "[[_raw/_archived/2026-10-18-qt-offscreen-no-x11|2026-10-18-qt-offscreen-no-x11]]"
---

# pytest-qt offscreen on macOS

[[synthesis/Research: Qt and Translation Workbench Best Practice]] left Qt's offscreen plugin unresolved: the Qt Test page says it is fully supported only on X11, while pytest-qt still suggests `QT_QPA_PLATFORM=offscreen` for CI. On the [[projects/aenglisc-toolkit/aenglisc-toolkit|aenglisc_toolkit]] tree, that platform does run without X11.

## What ran

`tests/conftest.py` sets `QT_QPA_PLATFORM=offscreen` before any PySide6 import. Seventeen test files use `qtbot`. On macOS, with `DISPLAY` unset, `QApplication.platformName()` returned `offscreen`. `tests/test_menus.py` and `tests/test_highlighting.py` passed 45 tests in 1.5 seconds. XQuartz is installed on that machine and was not used.

`offscreen` is its own platform plugin. This run did not need an X11 or Wayland display. The Qt Test sentence may be about how faithfully synthetic GUI events behave off X11, not about needing an X server installed. The Qt page was not re-read for this note, so that reading is a guess. ^[inferred]

## Pattern

Set `QT_QPA_PLATFORM=offscreen` at the top of `conftest.py`, before importing PySide6.

Linux and Windows CI were not run. The note expects Linux to need the xcb and fontconfig libraries the plugin loads. ^[inferred]

## Open Questions

- Does the same `conftest.py` pass the full suite, not only the two files?
- What fails on Linux without xcb and fontconfig, and on Windows?

## Sources

- [[_raw/_archived/2026-10-18-qt-offscreen-no-x11.md]]
