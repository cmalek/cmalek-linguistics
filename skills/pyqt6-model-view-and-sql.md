---
title: "Qt model/view, delegates, and SQL-backed editing"
category: "skills"
tags: ["qt", "pyqt", "gui", "python"]
sources: ["book:isbn:9781484279991/chapter/14"]
summary: "Separate data access, presentation, and editing; choose item models or SQL models according to the data source and the relationships being displayed."
provenance: {"extracted": 0.85, "inferred": 0.15, "ambiguous": 0}
base_confidence: 0.5667
lifecycle: "draft"
lifecycle_changed: "2026-10-18"
tier: "supporting"
created: "2026-10-18T19:59:31.689603+00:00"
updated: "2026-10-18T19:59:31.689603+00:00"
snapshots:
  - "[[_raw/_archived/14. Introduction to Handling Databases|14. Introduction to Handling Databases]]"
relationships:
  - target: "[[references/beginning-pyqt-willman-2022]]"
    type: derived_from
---

# Qt model/view, delegates, and SQL-backed editing

This note distills chapter 14 of [[references/beginning-pyqt-willman-2022|Willman’s Beginning PyQt]].

Chapter 14 moves beyond the item widgets of chapter 10. In its model/view account, the model interfaces with data, the view presents it, and the delegate handles item rendering and editors. Separating these roles lets more than one presentation use the same data model.

## Data-access choices

| Class or layer | Role demonstrated |
| --- | --- |
| Item model with QTableView | Present and edit structured data, including a CSV example |
| QSqlDatabase | Set up a database connection |
| QSqlQuery | Issue SQL and navigate results |
| QSqlTableModel | Expose one SQL table for viewing and editing |
| QSqlRelationalTableModel | Add support for foreign-key relationships |
| QSqlRelationalDelegate | Provide editors for related values, such as a country selector |

The examples include prepared inserts with bound values. The query discussion identifies failed execution and lastError as the route to inspecting an error; that error path remains part of the data-access boundary rather than something the view can infer from an empty display. ^[inferred]

## Relationships shown in the account-management example

Accounts and countries are represented in separate tables. The relational model associates a field with a lookup table, and the delegate offers a suitable editor for the displayed related value. This is an illustration of a SQL-backed UI, not a general substitute for an application’s domain model. ^[inferred]

[[skills/pyqt6-item-widgets-and-drag-drop]] explains the simpler bundled widgets. [[projects/aenglisc-toolkit/references/letos]] provides a larger data-workspace reference. [[projects/aenglisc-toolkit/skills/alembic-migration-service]] documents the application’s separate migration concerns; the chapter does not establish that its Qt SQL example should replace that stack. ^[inferred]

The sample database was not created or modified. Transactions, failure recovery, constraint coverage, and integration with an ORM were not validated by this ingest.

## Sources

- [[_raw/_archived/14. Introduction to Handling Databases.md]]
