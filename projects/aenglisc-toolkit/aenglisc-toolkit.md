---
title: >-
    aenglisc_toolkit
category: project
tags: [old-english, python, qt, pyside6, alembic, aenglisc-toolkit]
relationships:
  - target: "[[concepts/old-english]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-intent]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-current-capabilities]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-architecture]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-internal-improvements]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-documentation-audit]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-practice-gap-analysis]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-roadmap-trello]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/skills/alembic-migration-service]]"
    type: uses
  - target: "[[projects/aenglisc-toolkit/skills/qt-extraselection-highlight-layers]]"
    type: uses
  - target: "[[projects/aenglisc-toolkit/skills/pyside6-deploy-on-6-11]]"
    type: uses
  - target: "[[projects/aenglisc-toolkit/skills/pytest-qt-offscreen-macos]]"
    type: uses
sources:
  - "agent:aenglisc-toolkit-session-2026-10-02"
  - "agent:aenglisc-toolkit-session-2026-10-03"
  - "repo:/Users/cmalek/src/personal/aenglisc_toolkit @ 981e093 (v1.1.0)"
  - "url:https://trello.com/b/lEVKtPBa/aenglisc-toolkit"
  - "agent:aenglisc-toolkit-session-2026-10-18"
summary: >-
    Baseline for aenglisc_toolkit v1.1.0, a PySide6/SQLite manual Old English annotation and translation workbench: intent, features, architecture, verified internal and performance gaps, documentation audit, Qt-practice gaps, and the Trello board.
provenance:
  extracted: 0.75
  inferred: 0.22
  ambiguous: 0.03
base_confidence: 0.5
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-09T15:54:00Z
updated: 2026-10-20T15:55:46Z
snapshots:
  - "[[_raw/_archived/2026-10-03-aenglisc-alembic-migration-service-gotchas|2026-10-03-aenglisc-alembic-migration-service-gotchas]]"
  - "[[_raw/_archived/2026-10-02-qt-extraselection-highlight-layers|2026-10-02-qt-extraselection-highlight-layers]]"
  - "[[_raw/_archived/2026-10-02-git-squash-rebase-diverged-refactor|2026-10-02-git-squash-rebase-diverged-refactor]]"
  - "[[_raw/_archived/2026-10-18-pyside6-deploy-spec-only-config|2026-10-18-pyside6-deploy-spec-only-config]]"
  - "[[_raw/_archived/2026-10-18-qt-offscreen-no-x11|2026-10-18-qt-offscreen-no-x11]]"
---

# aenglisc_toolkit

A PySide6/SQLite desktop workbench (`oeapp`, version 1.1.0) for [[concepts/old-english]] reading, morphological annotation, notes and Modern English translation. Every linguistic decision is made by the translator; the app never auto-translates or auto-annotates. This is the author's first Qt application, and the pages below are a baseline for deciding where to apply Qt practice from other codebases. Research date 2026-10-18, repo HEAD `981e093`; nothing was profiled.

## The baseline

| Question | Page |
|---|---|
| What is it for? | [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-intent]] |
| What does it do now? | [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-current-capabilities]] |
| How is it built? | [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-architecture]] |
| What could be better internally, and faster? | [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-internal-improvements]] |
| How good are the global docs and in-app help? | [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-documentation-audit]] |
| Which Qt facilities are used, reimplemented or skipped? | [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-practice-gap-analysis]] |
| What is planned? | [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-roadmap-trello]] |
| How to replace hand-rolled code with stock Qt? | [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-idiom-plan]] |
| How to improve the UI flow, and what to drop? | [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ux-recommendations]] |
| How to produce academic-quality output? | [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-academic-output-plan]] |
| How to integrate with the OS? | [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-os-integration]] |
| Where may AI context appear? | [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ai-context-policy]] |
| Do remembered annotations bias the translator? | [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-remembered-annotations-and-bias]] |
| How to weigh macOS, Windows and Linux guidelines? | [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-cross-platform-conventions]] |
| What does `pyside6-deploy` read on 6.11.2? | [[projects/aenglisc-toolkit/skills/pyside6-deploy-on-6-11]] |
| Can pytest-qt run offscreen on macOS? | [[projects/aenglisc-toolkit/skills/pytest-qt-offscreen-macos]] |

## Headline findings

- **No background threading anywhere.** PDF export, DOCX, import and export, ingest, backups and migrations all run on the GUI thread (verified by grep).
- **A widget tree per sentence**, built eagerly for a whole section, with an extra `session.refresh` on every read render. Cost is unmeasured; it is the main scaling risk, and the planned chapter-at-a-time and all-text views would worsen it.
- **Per-keystroke undo commands** on the Modern English editor, with a 50-command cap and no merging, so typing evicts real history. Qt's `QUndoStack` supports merging and macros.
- **Autosave failures are swallowed** (printed, pending flag cleared) with no user-visible error.
- **Docs drift is already real:** the Keybindings help topic lists `Ctrl+Y` redo and global `J`/`K`, neither of which exists in code; two hand-written doc sets cover the same user topics.
- **Strong foundations:** ADR discipline, a domain glossary, SQLite tuning, a backup and migration safety path, a real `QAbstractTableModel`, a layer compositor for highlights, and about 1,080 tests.
- **Qt features not yet used:** `QUndoStack`, worker threads, saved window geometry and state, docks, delegates, proxy models, `QStandardPaths`, i18n, single-instance lock.

## Operational notes (from the early-October sessions)

- [[projects/aenglisc-toolkit/skills/alembic-migration-service]]: empty-DB policy is `create_all` plus stamp; `env.py` ignores an injected engine and follows `AENGLISC_TOOLKIT_DB_PATH`. ADR 0007 later fixed the backup and unknown-revision behaviour.
- [[projects/aenglisc-toolkit/skills/qt-extraselection-highlight-layers]]: one compositor owns `setExtraSelections`; layers are token anchors. Implemented in the editor by ADR 0004 (F3, Released); eleven `setExtraSelections` call sites remain, in `highlighting.py` and `full_translation_window.py`.
- [[skills/rebase-diverged-refactor]]: squash first when both sides refactored; clean auto-merges still broke `conftest` and `SentenceCard` construction.

## Related

- [[projects/aenglisc-toolkit/concepts/qt-app-design-references]]: seven Qt/desktop apps clipped as design references.
- [[references/fincept-terminal-qt-architecture]]: Qt patterns from a large C++/Qt app checked against this code.
- [[synthesis/Research: Qt and Translation Workbench Best Practice]]: external research (Qt docs, OS integration, desktop UX, translation tools) applied to the five pages above.
- [[projects/wyrdcraeft/wyrdcraeft]]: the morphology generator; a planned export target for a user-built dictionary, not this editor. ^[inferred]

## Open Questions

- Real load and interaction timings for a large section; whether the widget-per-sentence model needs virtualizing.
- Whether to adopt `QUndoStack` or keep the custom `CommandManager` and add merging.
- How to run workers safely given the single process-global SQLAlchemy session (F8).
- Which of the two doc sets becomes the single source for user topics.
- Empty-DB policy vs rewriting the baseline Alembic revision (still open on card F6).

## Sources

- Repo `README.md`, `CONTEXT.md`, `AGENTS.md`, `doc/source/**`, `oeapp/**`, `graphify-out/GRAPH_REPORT.md` (built at `9631ff93`, behind HEAD).
- Trello board *Ænglisc Toolkit* (52 cards), list meanings per the user.
- Qt 6 documentation pages listed on the gap-analysis page.
- [[_raw/_archived/2026-10-03-aenglisc-alembic-migration-service-gotchas.md]]
- [[_raw/_archived/2026-10-02-qt-extraselection-highlight-layers.md]]
- [[_raw/_archived/2026-10-02-git-squash-rebase-diverged-refactor.md]]
- [[_raw/_archived/2026-10-18-pyside6-deploy-spec-only-config.md]]
- [[_raw/_archived/2026-10-18-qt-offscreen-no-x11.md]]
