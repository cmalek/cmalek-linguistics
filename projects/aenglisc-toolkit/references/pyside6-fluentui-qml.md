---
title: "PySide6-FluentUI-QML: a QML component reference"
category: "references"
tags: ["qt", "pyside", "qml", "design"]
sources: ["repo:github.com/zhuzichu520/PySide6-FluentUI-QML"]
summary: "A clipped Fluent-design QML library with a C++ dependency, a Windows-only window component, and a migration notice."
provenance: {"extracted": 0.8, "inferred": 0.2, "ambiguous": 0}
base_confidence: 0.5917
lifecycle: "draft"
lifecycle_changed: "2026-10-18"
tier: "supporting"
created: "2026-10-18T19:48:28.152600+00:00"
updated: "2026-10-18T19:48:28.152600+00:00"
snapshots:
  - "[[_raw/_archived/GITHUB PySide6-FluentUI-QML 2026-10-18|GITHUB PySide6-FluentUI-QML 2026-10-18]]"
---

# PySide6-FluentUI-QML: a QML component reference

The captured README presents Fluent-design components for PySide6 and QML and points to a C++ FluentUI dependency. It also opens with a notice directing readers to FluentUI Pro; this records the snapshot’s guidance, not a current maintenance check.

| Component | Stated role or limitation |
| --- | --- |
| FluApp | Application entry with SPA routing |
| FluWindow | Frameless window; the table says Windows only |
| FluAppBar | Drag, minimize, maximize, and close |
| Text and button family | Text, standard, filled, text-only, and toggle buttons |
| Other controls | Icons and toggle switches |

The requirements line names Python 3.11. The README labels the library MIT and the documentation work in progress; the license file and dependency terms were not independently examined.

[[projects/aenglisc-toolkit/concepts/qt-app-design-references]] is the surrounding reading list. A QML component library offers a different implementation path from the app’s existing widgets, so visual inspiration does not establish drop-in compatibility. ^[inferred] [[concepts/ux-interface-selection]] supplies the user-centered question to ask before adopting a new interface stack.

## Sources

- [[_raw/_archived/GITHUB PySide6-FluentUI-QML 2026-10-18.md]]
