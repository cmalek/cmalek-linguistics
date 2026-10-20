---
title: "Qt offscreen platform runs pytest-qt without X11"
category: skills
tags:
  - topic/qt
  - pyside6
  - testing
  - aenglisc-toolkit
summary: "aenglisc_toolkit's pytest-qt suite runs on macOS with QT_QPA_PLATFORM=offscreen and no X11 or DISPLAY; the wiki's 'offscreen only on X11' worry does not hold there."
tier: supporting
related: []
extends: null
contradicts: "synthesis/Research: Qt and Translation Workbench Best Practice (Offscreen testing open question)"
superseded_by: null
capture_source: claude-session
project: "aenglisc-toolkit"
base_confidence: 0.75
lifecycle: draft
lifecycle_changed: 2026-10-18
provenance:
  extracted: 0.8
  inferred: 0.2
sources:
  - "aenglisc-toolkit session (2026-10-18)"
---

## Qt offscreen needs no X11

**Behavior:** The wiki's research page says Qt Test supports offscreen "only on X11", and leaves it unresolved. In `/Users/cmalek/src/personal/aenglisc_toolkit`, `tests/conftest.py` sets `QT_QPA_PLATFORM=offscreen` before any PySide6 import, and 17 test files use `qtbot`. On macOS with `DISPLAY` unset, `QApplication.platformName()` returned `offscreen`, and `tests/test_menus.py` plus `tests/test_highlighting.py` gave 45 passed in 1.5s. XQuartz is installed on the machine but nothing in the run used it.

**Explanation:** `offscreen` is its own platform plugin, so it needs neither X11 nor Wayland. The Qt Test wording probably concerns how faithfully synthesized GUI events behave on other platforms, not an X11 install requirement. That reading is a guess; the Qt page was not re-read. ^[inferred]

**Workaround / Pattern:** Set `QT_QPA_PLATFORM=offscreen` at the top of `conftest.py`, before importing PySide6.

**Confirmed by:** test pass on macOS (two test files, not the full suite).

**Notes:** Linux and Windows CI runs are unverified. Linux needs the xcb and fontconfig libraries the plugin loads. ^[inferred]
