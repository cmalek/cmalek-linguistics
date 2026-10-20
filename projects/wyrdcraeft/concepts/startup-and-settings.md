---
title: >-
    Startup and settings
category: concepts
tags: [old-english, python, wyrdcraeft]
relationships:
  - target: "[[projects/wyrdcraeft/wyrdcraeft]]"
    type: part_of
  - target: "[[projects/wyrdcraeft/concepts/dictionary-build]]"
    type: precedes
sources:
  - "repo:github.com/cmalek/wyrdcraeft"
summary: >-
    Every wyrdcraeft command loads Settings; the morphology and dictionary commands then pass a readiness gate that migrates or resets the canonical SQLite file.
provenance:
  extracted: 0.85
  inferred: 0.10
  ambiguous: 0.05
base_confidence: 0.59
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T16:50:00Z
updated: 2026-10-09T16:50:00Z
---

# Startup and settings

The root command builds one `Settings` object, stores it on the Click context, then runs the database readiness gate. Database commands assume that gate already ran. The gate is skipped for `version`, `settings`, `source`, and `diacritic` (`DATABASE_GATE_SKIP_COMMANDS` in `wyrdcraeft/cli/cli.py`), so those work with no database; only `morphology` and `dictionary` pass through it. Checked against the live repo on 2026-10-15 (HEAD 3b4915b). `wyrdcraeft settings` and `wyrdcraeft settings show` print the loaded values. `wyrdcraeft settings create` writes a `.wyrdcraeft.toml` file whose lines are JSON-encoded values, which is the current behavior of that command.

Flags such as `--verbose`, `--quiet`, `--config-file`, and `--output` are global. `--config-file` sets `WYRDCRAEFT_CONFIG_FILE` before settings load. Environment variables use the `WYRDCRAEFT_` prefix.

## Readiness gate

```mermaid
flowchart TD
    cli[CLI starts] --> settings[Load Settings]
    settings --> pending[Handle a pending backup]
    pending --> check[Look for canonical and legacy databases]
    check --> legacy{Legacy DB present and canonical missing}
    legacy -->|yes| backupLegacy[Back up the legacy file]
    backupLegacy --> fresh[Create a fresh canonical DB]
    fresh --> rebuild[Stop and ask for a rebuild]
    legacy -->|no| exists{Canonical file exists}
    exists -->|no| migrateNew[Apply Alembic migrations]
    exists -->|yes| revision{Alembic revision}
    revision -->|none| backupReset[Back up, reset, ask for a rebuild]
    revision -->|behind head| backupMigrate[Back up, then migrate]
    revision -->|at head| done[Continue the command]
```

The canonical path is `wyrdcraeft.sqlite3` under the app-data directory. An app-data override changes that location. A legacy morphology database beside it is backed up and replaced; the command then stops with rebuild instructions instead of silently converting the old file.

Schema readiness is not the same as a populated index. After migrate, `bt_*` and `forms` can still be empty until [[projects/wyrdcraeft/concepts/dictionary-build]] runs.
