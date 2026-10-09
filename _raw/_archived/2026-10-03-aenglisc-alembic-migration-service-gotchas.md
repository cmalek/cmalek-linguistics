---
title: aenglisc_toolkit MigrationService — Alembic chain not replayable; env.py ignores injected engine
tags: [python, alembic, sqlite, aenglisc-toolkit]
summary: Replaying Alembic upgrades on an empty DB fails at the first revision, and env.py ignores MigrationService's injected engine.
project: aenglisc_toolkit
base_confidence: 0.9
provenance:
  extracted: 0.9
  inferred: 0.1
lifecycle_changed: 2026-10-03
sources:
  - "aenglisc_toolkit session (2026-10-03)"
---

## Finding 1: Alembic chain cannot be replayed from an empty DB

- `command.upgrade(cfg, "head")` on an empty SQLite DB fails at the first revision:
  `Running upgrade -> 57399ca978ee, Initial schema` raises `NoSuchTableError: annotations`.
- The initial migration assumes tables already exist, so `create_all` + stamp head
  (`MigrationService.apply_migrations`, fresh-DB branch) is the only workable
  empty-DB policy without rewriting the baseline migration.
- Data-transform revisions (`merge_hyphenated_words`, `backfill_annotation_root_normalized_data`)
  have no rows to act on for an empty DB, so skipping them is harmless.
- Verified by running upgrade against a temp DB with `AENGLISC_TOOLKIT_DB_PATH` set,
  then diffing `sqlite_master` against a `Base.metadata.create_all` DB.

## Finding 2: env.py ignores the injected engine

- `oeapp/models/alembic/env.py` sets `sqlalchemy.url` from `get_project_db_path()`
  (env var `AENGLISC_TOOLKIT_DB_PATH`, else app-data path).
- `MigrationService(engine=...)` therefore only affects its own reads; `command.upgrade`,
  `_create_pre_migration_backup` and `_restore_pre_migration_backup` all act on the
  `get_project_db_path()` file. A custom engine can leave backup/restore pointed at a
  different file than the one being inspected.
- To test Alembic against a temp DB, set `AENGLISC_TOOLKIT_DB_PATH` before importing `oeapp`.

## Context

Trello card F6 (order 7/12): "MigrationService mixes Alembic, version catalog, and a second backup path".
Grilling in progress; first question (empty-DB policy) answered by this evidence.
