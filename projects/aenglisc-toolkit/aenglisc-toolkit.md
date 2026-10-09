---
title: >-
    aenglisc_toolkit
category: project
tags: [old-english, python, qt, alembic]
relationships:
  - target: "[[concepts/old-english]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/skills/alembic-migration-service]]"
    type: uses
  - target: "[[projects/aenglisc-toolkit/skills/qt-extraselection-highlight-layers]]"
    type: uses
sources:
  - "agent:aenglisc-toolkit-session-2026-10-02"
  - "agent:aenglisc-toolkit-session-2026-10-03"
summary: >-
    Qt/SQLite Old English annotation app: Alembic cannot replay from empty DB; ExtraSelection needs one compositor; a diverged refactor was squashed then rebased.
provenance:
  extracted: 0.80
  inferred: 0.15
  ambiguous: 0.05
base_confidence: 0.42
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T15:54:00Z
updated: 2026-10-09T15:54:00Z
snapshots:
  - "[[_raw/_archived/2026-10-03-aenglisc-alembic-migration-service-gotchas|2026-10-03-aenglisc-alembic-migration-service-gotchas]]"
  - "[[_raw/_archived/2026-10-02-qt-extraselection-highlight-layers|2026-10-02-qt-extraselection-highlight-layers]]"
  - "[[_raw/_archived/2026-10-02-git-squash-rebase-diverged-refactor|2026-10-02-git-squash-rebase-diverged-refactor]]"
---

# aenglisc_toolkit

A PySide/SQLite app for [[concepts/old-english]] reading and annotation (`oeapp`). Early-October 2026 sessions recorded three operational facts: migrations, editor highlights, and bringing a long-diverged refactor onto master.

## Key Concepts

- [[projects/aenglisc-toolkit/skills/alembic-migration-service]] — empty-DB policy is `create_all` + stamp; `env.py` ignores an injected engine and follows `AENGLISC_TOOLKIT_DB_PATH`.
- [[projects/aenglisc-toolkit/skills/qt-extraselection-highlight-layers]] — one compositor owns `setExtraSelections`; layer entries are token anchors, not stored cursors. Design reviewed, not implemented.
- [[skills/rebase-diverged-refactor]] — squash first when both sides refactored; clean auto-merges still broke `conftest` and `SentenceCard` construction.

## Related

- [[projects/wyrdcraeft/wyrdcraeft]] — morphology generator, not this editor. ^[inferred]
- Trello card F6 (order 7/12) framed MigrationService as mixing Alembic, a version catalog, and a second backup path.

## Open Questions

- Empty-DB policy vs rewriting the baseline Alembic revision (grilling in progress as of 2026-10-03).

## Sources

- [[_raw/_archived/2026-10-03-aenglisc-alembic-migration-service-gotchas.md]]
- [[_raw/_archived/2026-10-02-qt-extraselection-highlight-layers.md]]
- [[_raw/_archived/2026-10-02-git-squash-rebase-diverged-refactor.md]]
