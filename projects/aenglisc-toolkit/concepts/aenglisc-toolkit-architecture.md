---
title: >-
  aenglisc_toolkit: architecture
category: concepts
tags: [aenglisc-toolkit, architecture, pyside6, sqlalchemy, alembic]
relationships:
  - target: "[[projects/aenglisc-toolkit/aenglisc-toolkit]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-current-capabilities]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-internal-improvements]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/skills/alembic-migration-service]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/skills/qt-extraselection-highlight-layers]]"
    type: related_to
sources:
  - "repo:/Users/cmalek/src/personal/aenglisc_toolkit @ 981e093"
  - "repo: AGENTS.md, doc/source/architecture/adr_0001..0007, graphify-out/GRAPH_REPORT.md (built 2026-10-04 at 9631ff93)"
summary: >-
  Layered PySide6 desktop app: fat SQLAlchemy models, thin services, an undoable Command layer, one process-global session, and a UI dominated by two very large modules (MainWindow and SentenceCard) that the Trello audit cards are splitting.
provenance:
  extracted: 0.82
  inferred: 0.18
  ambiguous: 0.0
base_confidence: 0.55
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T20:10:00Z
updated: 2026-10-18T20:10:00Z
---

# aenglisc_toolkit: architecture

## Package layout (`oeapp/`)

| Package | Role | Notable files (lines) |
|---|---|---|
| `main.py`, `ui/application.py` | Entry point; builds `QApplication`, theme, fonts, `MainWindow` | |
| `models/` | SQLAlchemy ORM (fat models) plus Pydantic schemas; Alembic under `models/alembic` | `project.py` 979, `token.py` 886, `sentence.py` 919, `annotation.py` 736 |
| `services/` | Business workflows: backup, migration, import/export, DOCX/PDF/text export, propagation, remembered annotations, Wyrdcraeft ingest, autosave, logging | `export_pdf.py` 1522, `migration.py` 961, `wyrdcraeft_ingest.py` 716, `import_export.py` 681 |
| `commands/` | Undoable operations on a `Command` ABC with a `CommandManager` | `sentence.py` 679, `hierarchy.py` 645 |
| `ui/` | Widgets, controllers, dialogs, highlighting | `main_window.py` 1774, `full_translation_window.py` 1567, `oe_text_edit.py` 1537, `sentence_card.py` 1186, `highlighting.py` 1008 |
| `help/` | QtHelp engine wrapper and topic registry; sources in `help/topics/*.md`, built to `help/assets/*.qch/.qhc` | |
| `state.py`, `db.py`, `mixins.py`, `utils.py` | `AppContext`, engine/session setup and SQLite PRAGMAs, shared lookup maps | |

Stated rules (`AGENTS.md`): models in `oeapp.models`; business logic in `oeapp.services`; all UI and wiring in `oeapp.ui`; "FAT ORM" with DB operations on the model; methods at most 60 lines; constructor injection; every model change needs an Alembic migration; a Napoleon-style docstring gate (`make napoleon-gate`).

## Runtime shape

```
main.py -> create_application() -> MainWindow
  MainWindow.__init__:
     BackupService, _handle_migrations() (backup -> alembic -> restore on failure),
     run_pragma_optimize(), AppContext, MainWindowActions, AutosaveService
  build(): toolbars + QScrollArea of SentenceCards | QSplitter | TokenDetailsSidebar
           ProjectUI (workspace), MainMenu, GlobalShortcuts
  ProjectUI.load_section(): one SentenceCard per sentence, all added to one layout
```

- **State**: `AppContext(QObject)` holds app-lifetime state (current project/chapter/section ids, the Copied Annotation, `QSettings`, the `CommandManager`) and emits signals on change. Transient selection belongs to workspace and controllers.
- **Persistence**: one SQLAlchemy `Session` stored in a module global (`db._RUNTIME_STATE`), reached by models through `cls._get_session()` and by `AppContext.session`. Trello F8 records this as accepted-but-frozen: no new `_get_session()` call sites, inject into touched services. There are about 52 `commit()` call sites.
- **Undo**: custom `Command` ABC (`execute`, `undo`, `get_description`, `needs_full_reload`) and a `CommandManager` with list-based undo/redo stacks capped at 50 and a re-entrancy guard. Commands mutate the DB through the shared session.
- **Events**: 37 `Signal(...)` declarations in 9 files and about 211 `.connect(...)` calls; global shortcuts are `QShortcut`s attached to the main window.
- **Highlighting**: `OldEnglishTextEdit` owns a `HighlightLayers` compositor with mode, span and search layers (ADR 0004, [[projects/aenglisc-toolkit/skills/qt-extraselection-highlight-layers]]). Eleven `setExtraSelections` call sites remain: one in the compositor, four in `highlighting.py`, six in `full_translation_window.py`.
- **Forms**: `PosFieldCatalog` (UI-only data) drives modal, preset dialog and sidebar renderers (ADR 0005).
- **Export**: services build output directly; PDF writes LaTeX and shells out to Tectonic with `subprocess.run` (`services/pdf_engine.py`).
- **Help**: `HelpEngine` wraps `QHelpEngine`; the packaged `.qch`/`.qhc` are copied to the user data dir and registered; full-text indexing is requested when the engine is created. The help is built at build time, not startup (Trello, Released).
- **Migrations**: `MigrationService` plus `BackupService` plus `revision_version` catalog; policy decided in ADR 0007 (BackupService is the only backup collaborator; "Pending Migration" is decided by the Alembic revision comparison only).
- **Paths**: `get_app_data_path()` honours `AENGLISC_TOOLKIT_DATA_PATH`, else uses Application Support (macOS), `AppData/Local` (Windows) and `~/.config` (Linux). Qt's `QStandardPaths` is not used.

## Design decisions on record (ADRs, `doc/source/architecture/`)

| ADR | Decision |
|---|---|
| 0001 | Usability overhaul on one long-lived integration branch |
| 0002 | Undoing an idiom creation deletes the Idiom (and its Annotation) |
| 0003 | One Export submenu: Project file, Old English, Translation |
| 0004 | The editor owns the merged ExtraSelection list; three layers with fixed stacking |
| 0005 | UI-only POS field catalog; ORM remains authority on allowed codes |
| 0006 | Copied Annotation held as validated `AnnotationJson`, validated at the setter |
| 0007 | BackupService is the sole backup path; unknown-revision refusal; restore refuses newer backups |

Trello card F13 notes ADR location is inconsistent: some plans refer to `docs/adr/` while `AGENTS.md` mandates RST in `doc/source/architecture/`.

## Structural hot spots (from graphify and the audit cards)

- `MainWindow` (95 graph edges) and `MainWindowActions` (about 840 lines inside `main_window.py`) are a multi-concern façade: export, backup, search, paste, autosave, migrations. Card F1.
- `SentenceCard` (172 edges, 76 commits) still mixes layout, search chrome, notes, hierarchy and annotation apply, with a controller split that moved files, not boundaries. Card F7.
- `FullTranslationPDFExporter` mixes I/O, LaTeX emission and glossary logic. Card F9.
- `MigrationService` mixed Alembic, a version catalog and a second backup path. Card F6, now Doing.
- Graph snapshot: 6,379 nodes, 12,302 edges, 349 communities, built from commit `9631ff93` on 2026-10-04, so it is behind HEAD (version 1.1.0). Run `graphify update .` before relying on it.

## Dependencies worth knowing

PySide6 6.6+, SQLAlchemy 2, Alembic, Pydantic 2, `qt-themes`, `qtpy` (imported only by `ui/highlighting.py`), `python-docx`, `markdown` (help build), `structlog`, `setproctitle` (macOS menu name), and `wyrdcraeft` (which pulls a very large optional tree via `unstructured[all-docs]`; the app only reads text formats, and `pyproject.toml` has a note about excluding the heavy extras).

## Sources

Repo files in the front matter; Trello cards F1 to F13; Qt docs consulted for comparison on [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-practice-gap-analysis]].
