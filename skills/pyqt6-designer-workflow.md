---
title: "Qt Designer forms and separate application behavior"
category: "skills"
tags: ["qt", "pyqt", "gui", "python"]
sources: ["book:isbn:9781484279991/chapter/8"]
summary: "Create and preview a .ui form, generate its Python interface class, and place application behavior in a separate script."
provenance: {"extracted": 0.8, "inferred": 0.15, "ambiguous": 0.05}
base_confidence: 0.5667
lifecycle: "draft"
lifecycle_changed: "2026-10-18"
tier: "supporting"
created: "2026-10-18T19:59:31.689603+00:00"
updated: "2026-10-18T19:59:31.689603+00:00"
snapshots:
  - "[[_raw/_archived/8. Creating GUIs with Qt Designer|8. Creating GUIs with Qt Designer]]"
relationships:
  - target: "[[references/beginning-pyqt-willman-2022]]"
    type: derived_from
---

# Qt Designer forms and separate application behavior

This note distills chapter 8 of [[references/beginning-pyqt-willman-2022|Willman’s Beginning PyQt]].

Chapter 8 introduces Qt Designer as a visual way to arrange widgets, set properties, assign layouts, connect signals and slots, and preview a form. The saved `.ui` document is then used to produce Python interface code.

## The keypad example’s artifacts

| Artifact | Responsibility |
| --- | --- |
| .ui form | Visual object tree, properties, and configured connections |
| Generated UI module | Ui_Keypad and setupUi |
| Application module | Create the window, instantiate the UI helper, and add behavior |

The project’s actual MainWindow example inherits QWidget, creates a Ui_Keypad instance, and calls its setupUi method. Its behavior is added in a separate file. Keeping those roles apart lets the form remain an editable input to generation.

## Source inconsistency

One prose passage says the application class will inherit Ui_Keypad, but the displayed example uses composition with a QWidget subclass. These describe different structures. This note follows the shown example and records the discrepancy rather than combining them into one recipe. ^[ambiguous]

[[skills/pyqt6-layout-management]] covers the layouts that Designer assigns. [[skills/ux-prototyping]] explains the purpose of making a design concrete for feedback. [[projects/aenglisc-toolkit/concepts/qt-app-design-references]] offers other ways to study desktop design without requiring a move to Designer.

The chapter’s installation options and generation commands are historical instructions. They were not run or checked against the current toolchain.

## Sources

- [[_raw/_archived/8. Creating GUIs with Qt Designer.md]]
