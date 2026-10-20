---
title: "Qt item widgets, tables, trees, and drag-and-drop"
category: "skills"
tags: ["qt", "pyqt", "gui", "python"]
sources: ["book:isbn:9781484279991/chapter/10"]
summary: "Convenience widgets combine storage and presentation for lists, tables, and trees; drag-and-drop additionally needs compatible transfer behavior."
provenance: {"extracted": 0.8, "inferred": 0.15, "ambiguous": 0.05}
base_confidence: 0.5667
lifecycle: "draft"
lifecycle_changed: "2026-10-18"
tier: "supporting"
created: "2026-10-18T19:59:31.689603+00:00"
updated: "2026-10-18T19:59:31.689603+00:00"
snapshots:
  - "[[_raw/_archived/10. Presenting Data in PyQt|10. Presenting Data in PyQt]]"
relationships:
  - target: "[[references/beginning-pyqt-willman-2022]]"
    type: derived_from
---

# Qt item widgets, tables, trees, and drag-and-drop

This note distills chapter 10 of [[references/beginning-pyqt-willman-2022|Willman’s Beginning PyQt]].

Chapter 10 introduces item-based convenience widgets before chapter 14 separates models, views, and delegates. These convenience classes package common data-display behavior with their own item objects.

## Match the representation to the relationship

| Display | Widget | Item class |
| --- | --- | --- |
| One list of entries | QListWidget | QListWidgetItem |
| Rows and columns | QTableWidget | QTableWidgetItem |
| Parent–child hierarchy | QTreeWidget | QTreeWidgetItem |

The table example adds editable cells, headers, context menus, and operations on selected data. The tree example makes parent–child relationships visible, including items with several displayed columns. A tree’s hierarchy is its distinguishing structure.

Drag-and-drop moves compatible data between supporting widgets. The chapter enables drag and drop for its list examples and identifies QMimeData as the mechanism for describing transferable formats. The example’s two settings should not be read as a complete implementation of every custom drop target. ^[inferred]

[[skills/pyqt6-model-view-and-sql]] covers the next architectural step when data and displays need to be separated. [[concepts/ux-interface-selection]] helps choose the representation, while [[projects/aenglisc-toolkit/references/letos]] is an existing reference for a data-oriented Qt workspace.

## Source qualification

Chapter 14’s recap incorrectly labels a table entry QTreeWidget while also listing QTreeWidget as hierarchical. This note retains chapter 10’s explicit distinction between QTableWidget and QTreeWidget. ^[ambiguous]

## Sources

- [[_raw/_archived/10. Presenting Data in PyQt.md]]
