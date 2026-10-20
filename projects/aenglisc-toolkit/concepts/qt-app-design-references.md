---
title: >-
  Qt app design references
category: concepts
tags: [qt, design, desktop-app, references]
relationships:
  - target: "[[projects/aenglisc-toolkit/aenglisc-toolkit]]"
    type: related_to
sources:
  - "book:isbn:9781484279991/chapter/15"
  - "book:isbn:9781484279991/chapter/14"
  - "repo:github.com/zhuzichu520/PySide6-FluentUI-QML"
  - "url:https://github.com/pawelsalawa/letos"
  - "url:https://github.com/musescore/MuseScore"
  - "url:https://github.com/eyllanesc/QtExamples"
  - "url:https://github.com/ahatem/QTranslate"
  - "url:https://github.com/spyder-ide/qtsass"
  - "url:https://github.com/qutebrowser/qutebrowser"
  - "url:https://github.com/Serial-Studio/Serial-Studio"
summary: "Desktop application and QML component references for aenglisc_toolkit, with links to user-research and evaluation methods."
provenance:
  extracted: 0.6
  inferred: 0.4
  ambiguous: 0.0
base_confidence: 0.42
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: peripheral
created: 2026-10-18T18:08:52Z
updated: "2026-10-18T19:59:31.689603+00:00"
snapshots:
  - "[[_raw/_archived/GITHUB MuseScore 2026-10-17|GITHUB MuseScore 2026-10-17]]"
  - "[[_raw/_archived/GITHUB QTranslate 2026-10-18|GITHUB QTranslate 2026-10-18]]"
  - "[[_raw/_archived/GITHUB QtExamples 2026-10-18|GITHUB QtExamples 2026-10-18]]"
  - "[[_raw/_archived/GITHUB Serial-Studio 2026-10-17|GITHUB Serial-Studio 2026-10-17]]"
  - "[[_raw/_archived/GITHUB letos 2026-10-18|GITHUB letos 2026-10-18]]"
  - "[[_raw/_archived/GITHUB qtsass 2026-10-17|GITHUB qtsass 2026-10-17]]"
  - "[[_raw/_archived/GITHUB qutebrowser 2026-10-17|GITHUB qutebrowser 2026-10-17]]"
  - "[[_raw/_archived/GITHUB PySide6-FluentUI-QML 2026-10-18|GITHUB PySide6-FluentUI-QML 2026-10-18]]"
  - "[[_raw/_archived/14. Introduction to Handling Databases|14. Introduction to Handling Databases]]"
  - "[[_raw/_archived/15. Managing Threads|15. Managing Threads]]"
---

# Qt app design references

A reading list of desktop applications clipped from GitHub on 2026-10-17 and 2026-10-18, all tagged `qt` and mostly `design` in the clippings. The clippings do not say why they were saved; the link to [[projects/aenglisc-toolkit/aenglisc-toolkit|aenglisc_toolkit]], a Qt/SQLite Old English annotation app, is an inference from the shared stack. ^[inferred]

## The Seven

| App | Stack | What it shows |
|---|---|---|
| [[projects/aenglisc-toolkit/references/letos\|Letos]] | C++/Qt | A mature SQLite front end |
| [[projects/aenglisc-toolkit/references/musescore\|MuseScore Studio]] | C++/QML | WYSIWYG specialist document editor with open interchange formats |
| [[projects/aenglisc-toolkit/references/qtexamples\|QtExamples]] | Python | C++ Qt idioms ported to PyQt5/PySide2 |
| [[projects/aenglisc-toolkit/references/qtranslate\|QTranslate]] | Kotlin | Select-then-lookup flow; plugin boundary around every external service |
| [[projects/aenglisc-toolkit/references/qtsass\|QtSASS]] | Python | SASS variables and nesting for Qt stylesheets |
| [[projects/aenglisc-toolkit/references/qutebrowser\|qutebrowser]] | Python/Qt | Keyboard-first PyQt application |
| [[projects/aenglisc-toolkit/references/serial-studio\|Serial Studio]] | C/C++/QML | Declarative project file driving the dashboard |

## Patterns Across Them

- Two apps put an external boundary around volatile things: QTranslate wraps every service as a plugin, and Serial Studio puts parsers behind built-in, JavaScript or Lua templates. ^[inferred]
- Two keep the UI definition in data rather than code: Serial Studio's project file and QtSASS's stylesheet source. ^[inferred]
- QTranslate is the only entry that is not a Qt application; it is a lookup-UX reference. ^[inferred]

## Related

- [[projects/aenglisc-toolkit/skills/qt-extraselection-highlight-layers]] — the toolkit's own Qt editor-highlight notes.
- [[concepts/old-english]] — the domain the toolkit serves.

## Additional component reference

[[projects/aenglisc-toolkit/references/pyside6-fluentui-qml]] adds a Fluent-design QML component library. Its snapshot flags a C++ dependency, a Windows-only frameless window component, and a successor notice; it needs a separate compatibility assessment before reuse. [[references/interaction-design-5th-edition]] now supplies a general method for investigating user needs and evaluating the resulting interface. ^[inferred]

## PyQt6 learning guide

[[references/beginning-pyqt-willman-2022]] adds a chapter-by-chapter learning route through widget construction, layouts, actions, events, data views, painting, QML, SQL, and background work.

[[skills/pyqt6-model-view-and-sql]] and [[skills/pyqt6-responsive-background-work]] are useful companions to the existing data-workspace and responsiveness notes. The book’s examples are instructional; they do not establish that the toolkit should replace its database layer, adopt QML, or copy the sample worker’s cancellation method. ^[inferred]

## Sources

The seven clippings are listed on their individual pages.
- [[_raw/_archived/GITHUB PySide6-FluentUI-QML 2026-10-18.md]]
- [[_raw/_archived/14. Introduction to Handling Databases.md]]
- [[_raw/_archived/15. Managing Threads.md]]
