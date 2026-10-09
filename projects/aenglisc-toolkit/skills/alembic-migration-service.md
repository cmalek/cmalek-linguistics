---
title: >-
    aenglisc MigrationService Alembic Gotchas
category: skills
tags: [python, alembic, sqlite]
relationships:
  - target: "[[projects/aenglisc-toolkit/aenglisc-toolkit]]"
    type: related_to
sources:
  - "agent:aenglisc-toolkit-session-2026-10-03"
summary: >-
    Replaying Alembic on an empty SQLite DB fails at the first revision; env.py ignores MigrationService’s injected engine and uses AENGLISC_TOOLKIT_DB_PATH.
provenance:
  extracted: 0.90
  inferred: 0.10
  ambiguous: 0.00
base_confidence: 0.42
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T15:54:00Z
updated: 2026-10-09T15:54:00Z
snapshots:
  - "[[_raw/_archived/2026-10-03-aenglisc-alembic-migration-service-gotchas|2026-10-03-aenglisc-alembic-migration-service-gotchas]]"
---

# aenglisc MigrationService Alembic Gotchas

Two facts about [[projects/aenglisc-toolkit/aenglisc-toolkit]] `MigrationService`, verified against a temp DB.

## Key Ideas

**The Alembic chain cannot be replayed from empty.** `command.upgrade(cfg, "head")` on empty SQLite fails at `Running upgrade -> 57399ca978ee, Initial schema` with `NoSuchTableError: annotations`. The initial revision assumes tables already exist. Fresh-DB policy that works without rewriting the baseline: `create_all` then stamp head (`MigrationService.apply_migrations` empty-DB branch). Data-transform revisions (`merge_hyphenated_words`, `backfill_annotation_root_normalized_data`) have nothing to do on an empty DB, so skipping them is harmless.

Verified by upgrading a temp DB with `AENGLISC_TOOLKIT_DB_PATH` set, then diffing `sqlite_master` against `Base.metadata.create_all`.

**`env.py` ignores the injected engine.** `oeapp/models/alembic/env.py` sets `sqlalchemy.url` from `get_project_db_path()` (`AENGLISC_TOOLKIT_DB_PATH`, else app-data). `MigrationService(engine=...)` only affects its own reads. `command.upgrade`, `_create_pre_migration_backup`, and `_restore_pre_migration_backup` all act on the path file. A custom engine can point backup/restore at a different file than the one being inspected. To test Alembic against a temp DB, set `AENGLISC_TOOLKIT_DB_PATH` **before importing** `oeapp`.

## Open Questions

- Whether to rewrite the baseline revision so `upgrade` from empty is legal, vs keeping stamp-on-create (Trello F6 / grilling). ^[ambiguous]

## Sources

- [[_raw/_archived/2026-10-03-aenglisc-alembic-migration-service-gotchas.md]]
