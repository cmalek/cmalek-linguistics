---
title: >-
  QtSASS (SASS to Qt stylesheets)
category: references
tags: [qt, python, stylesheet, design]
sources:
  - "url:https://github.com/spyder-ide/qtsass"
summary: >-
  QtSASS compiles SASS to Qt stylesheets by preprocessing two Qt-only syntaxes: ':!' negated states and qlineargradient().
provenance:
  extracted: 0.67
  inferred: 0.33
  ambiguous: 0.0
base_confidence: 0.47
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: peripheral
created: 2026-10-18T18:08:40Z
updated: 2026-10-18T18:08:40Z
snapshots:
  - "[[_raw/_archived/GITHUB qtsass 2026-10-17|GITHUB qtsass 2026-10-17]]"
---

# QtSASS (SASS to Qt stylesheets)

QtSASS bridges SASS and Qt's CSS dialect so a Qt app can be styled from a valid SASS file. Maintained under spyder-ide (150 stars at clip time; 89.5% Python).

## Key Points

- Qt allows negated widget states such as `QLineEdit:!editable`, which is invalid SASS. QtSASS rewrites `:!` to `:_qnot_` before compiling and restores `:!` in the output. This makes the source file not strictly valid SASS, and the README warns the behaviour may change.
- `qlineargradient(x1: 0, y1: 0, x2: 0, y2: 1, stop: 0.1 blue, stop: 0.8 green)` is invalid CSS syntax. QtSASS supplies a SASS implementation taking the stops as a list, e.g. `qlineargradient(0, 0, 0, 1, (0.1 blue, 0.8 green))`, so variables can hold the stops.
- Relevance to [[projects/aenglisc-toolkit/aenglisc-toolkit|aenglisc_toolkit]]: gives a theme the variables and nesting that plain QSS lacks. ^[inferred]

Part of [[projects/aenglisc-toolkit/concepts/qt-app-design-references|Qt app design references]].

## Sources

- [[_raw/_archived/GITHUB qtsass 2026-10-17]] — clipping of https://github.com/spyder-ide/qtsass (2026-10-17)
