---
title: "Qt main windows, shared actions, and dialogs"
category: "skills"
tags: ["qt", "pyqt", "gui", "python"]
sources: ["book:isbn:9781484279991/chapter/5"]
summary: "QMainWindow organizes a central widget, menus, toolbars, docks, and status feedback; QAction connects several command entry points."
provenance: {"extracted": 0.85, "inferred": 0.15, "ambiguous": 0}
base_confidence: 0.5667
lifecycle: "draft"
lifecycle_changed: "2026-10-18"
tier: "supporting"
created: "2026-10-18T19:59:31.689603+00:00"
updated: "2026-10-18T19:59:31.689603+00:00"
snapshots:
  - "[[_raw/_archived/5. Menus, Toolbars, and More|5. Menus, Toolbars, and More]]"
relationships:
  - target: "[[references/beginning-pyqt-willman-2022]]"
    type: derived_from
---

# Qt main windows, shared actions, and dialogs

This note distills chapter 5 of [[references/beginning-pyqt-willman-2022|Willman’s Beginning PyQt]].

Chapter 5 moves from a general widget window to `QMainWindow`, with dedicated places for the primary content, menu bar, toolbars, docks, and status feedback. The notepad and photo-editor examples assemble these features into a desktop workspace.

## Separate the command from its presentation

| Part | Role in the examples |
| --- | --- |
| QAction | A command with text, shortcut, icon, or checkable state |
| Menu | Organize commands and submenus |
| QToolBar | Quick access to frequent actions |
| QDockWidget | Movable or floating secondary tools |
| QStatusBar | Feedback and contextual information |
| Central widget | The main editing or viewing surface |

The chapter reuses an action through different entry points, so a menu item, toolbar button, or shortcut can invoke the same command. A general QWidget container can hold a layout before becoming the main window’s central widget.

## Dialogs and outcomes

The examples use QFileDialog for file selection, QInputDialog for a value, QFontDialog and QColorDialog for appearance choices, and QMessageBox for feedback. Selection and cancellation must be interpreted according to the dialog’s return value; the chapter demonstrates checking accepted input and valid colors.

[[concepts/ux-conceptual-models]] helps organize the command vocabulary, while [[concepts/ux-cognition]] connects feedback to a user’s interpretation of what happened. [[projects/aenglisc-toolkit/concepts/qt-app-design-references]] collects larger applications in which these workspace patterns can be studied.

The examples demonstrate interface mechanics; their file-saving paths were not executed or audited as production persistence code.

## Sources

- [[_raw/_archived/5. Menus, Toolbars, and More.md]]
