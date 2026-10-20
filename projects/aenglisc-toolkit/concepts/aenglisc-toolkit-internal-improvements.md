---
title: >-
  aenglisc_toolkit: internal improvements and performance
category: concepts
tags: [aenglisc-toolkit, performance, refactoring, pyside6, technical-debt]
relationships:
  - target: "[[projects/aenglisc-toolkit/aenglisc-toolkit]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-architecture]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-practice-gap-analysis]]"
    type: related_to
  - target: "[[references/fincept-terminal-qt-architecture]]"
    type: related_to
sources:
  - "repo:/Users/cmalek/src/personal/aenglisc_toolkit @ 981e093 (read 2026-10-18)"
  - "url:https://trello.com/b/lEVKtPBa/aenglisc-toolkit"
summary: >-
  Code-evidenced improvement list for aenglisc_toolkit: no background threads anywhere, one widget tree per sentence, per-keystroke undo commands that evict real history, silent autosave failures, and several correctness and portability gaps; findings are marked verified or unmeasured.
provenance:
  extracted: 0.65
  inferred: 0.35
  ambiguous: 0.0
base_confidence: 0.45
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T20:15:00Z
updated: 2026-10-18T20:15:00Z
---

# aenglisc_toolkit: internal improvements and performance

Evidence grades: **verified** means read in code or confirmed by grep on 2026-10-18; **unmeasured** means plausible from the code but never profiled. No profiling was run. Items already tracked on Trello are tagged with their card. Qt-feature adoption is covered separately in [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-practice-gap-analysis]].

## Performance

| # | Finding | Evidence | Grade | Suggested direction |
|---|---|---|---|---|
| P1 | **Everything runs on the GUI thread.** A grep of `oeapp` for `QThread`, `QRunnable`, `QThreadPool`, `QtConcurrent`, `moveToThread` and `QProcess` returns nothing. PDF export calls Tectonic via synchronous `subprocess.run` from `FullTranslationWindow._export_pdf`. DOCX, JSON import/export, Wyrdcraeft ingest, backups and migrations also run in the UI thread. | grep; `full_translation_window.py:1374-1389`; `services/pdf_engine.py:178` | verified | `QThreadPool` + `QRunnable` (or `QProcess` for Tectonic) with signals to report progress; a `QProgressDialog` for export. Card F9 mentions an optional worker. |
| P2 | **One widget tree per sentence, no virtualization.** `ProjectUI.load_section` builds a `SentenceCard` for every sentence in the section and adds each to one layout. Each card holds a read-only `OldEnglishTextEdit`, a Modern English `QTextEdit`, a `NotesPanel`, a token table toggle, and buttons. Cost scales with section size. A Backlog card wants whole-text and chapter-at-a-time views, which would multiply it. | `project_workspace.py:158-192`; Trello "view modes" | cost shape verified, magnitude unmeasured | Profile load time on the largest real section first. Options: lazy-create cards as they scroll into view; or one model/view (`QListView` + delegate) for read mode with an editor widget only on the active sentence. |
| P3 | **Extra queries on every render.** `OldEnglishTextEdit.render_readonly_text` calls `session.refresh(sentence, ["notes","idioms","tokens"])` on every read-only render. Each card also schedules its render with `QTimer.singleShot(0, ...)`, so a section load queues N deferred renders. | `oe_text_edit.py:948-954`, `:565` | verified | Eager-load relationships once when fetching the section (`selectinload`), then render without refresh; refresh only after a command invalidates. |
| P4 | **Per-keystroke undo commands.** `textChanged` on the Modern English editor runs `EditSentenceCommand` on each change. `CommandManager.execute` appends every command and drops the oldest past 50, with no merge. Typing 50 characters can evict all earlier undo history. | `sentence_card.py:583`; `sentence_card_controller.py:127-146`; `commands/abstract.py` | verified (behaviour), harm inferred | Debounce or commit on focus-out (card F7 recommends this); or adopt command merging as `QUndoStack` does (`id()` + `mergeWith()`). |
| P4b | **Autosave timer churn.** `AutosaveService.trigger` stops, `deleteLater()`s and constructs a new `QTimer` on every call. | `services/autosave.py:41-53` | verified, impact small | Keep one single-shot `QTimer` and call `start()` to restart it. |
| P5 | **Settings read in hot paths.** Highlighting code reads `QSettings("theme/name")` when computing colours, and `sentence_card.py` defaults the same key to `"nord"` while `application.py` defaults it to `"dark"`. | `highlighting.py:868,962`; `sentence_card.py:240`; `application.py:35` | verified, impact small | Derive colours from the application `QPalette`, which `qt_themes.set_theme` already sets, and drop the settings reads. |
| P6 | **Startup does synchronous work before the window shows.** `MainWindow.__init__` runs migration (with backup), `PRAGMA optimize` and an initial backup check before building the UI, then the first section builds all cards. | `main_window.py:111-135`, `:625-632` | verified, cost unmeasured | Time cold start. If large: show the window first, run migration with a splash/progress dialog, defer the first backup check. |
| P7 | SQLite tuning is already done well: WAL, `synchronous=NORMAL`, 16 MiB cache, 128 MiB mmap, memory temp store, tunable by env vars, composite indexes on hierarchy tables, an index test (`test_db_indexes.py`). | `db.py` | verified | Keep. Add indexes only after a slow query is observed. |

## Correctness and data safety

- **Silent autosave failure.** `AutosaveService._save` catches `Exception`, `print()`s it, and sets `_pending = False`; `save_now` also only prints. The user is never told a save failed. Route the error to the logger and a visible status message, and keep the pending flag set. (verified, `autosave.py:75-102`)
- **Remembered annotations skip capitalized and line-initial words.** Four On Deck cards describe it (*Hē*, *Hī* not matched; words at line start cannot be copied). The glossary says matching is on exact surface text, so the matching key likely needs the Normalized Form, or a case-insensitive lookup. ^[inferred]
- **Paste is not undoable** (On Deck). ADR 0006 holds the Copied Annotation in `AppContext`, so a paste command would follow the existing `AnnotateTokenCommand`.
- **Stale CHECK constraints** (On Deck). On the maintainer's live database `annotations` had 1 CHECK where the model declares about 20, and rows exist that violate the declared checks (6 rows `declension='Strong (s)'`, 31 rows `declension=''`). Alembic autogenerate does not track CHECKs. Needs a repair-then-constrain migration and a test that fails when a model CHECK changes without a revision.
- **Process-global session.** `db._RUNTIME_STATE.session`, models calling `cls._get_session()`, about 52 `commit()` sites and 8 session uses inside `ui/`. Card F8 chooses "freeze and inject" over a rewrite; a stale identity map after commands is the suspected failure mode.
- **No single-instance guard.** Troubleshooting tells users that two instances "can conflict" on the SQLite file, yet nothing prevents launching a second one (no `QLockFile` or `QSharedMemory`). A `QLockFile` in the data dir is a few lines.
- **Autosave "Note FK sanitization"** was moved off the window (Released), but paste and migrations still live in UI code (F1).

## Structure and maintainability

- F1 `MainWindowActions` split; F7 finish the `SentenceCard` controller split (annotation apply off the widget, no new DB reads in UI, remove the card-controller `_open_*_modal` bounce); F8 session freeze; F9 split glossary aggregation from LaTeX emission in `export_pdf.py` (dead `_group_sentences_by_paragraph` flagged); F10 test ownership (about 16 token-test files, `application.py` at 0% coverage). Order is set on the cards.
- Huge dialog methods (Backlog "refactor all the dialogs"). The 60-line rule exists; `annotation_modal.py` (945), `annotation_preset_management.py` (953) and `pos_form_system.py` (690) are the big ones.
- Pragmatic debt in `application.py`: a `QSystemTrayIcon` is created, held only in a local variable, and shows a "Welcome" notification on every launch; an unused `families` variable; the font list names `Anvers-SemiBold.ttf` while the file on disk is `Anvers-Semibold.ttf`, which silently fails to load on a case-sensitive filesystem (Linux) because the loader skips missing paths. `DOE.ttf` ships in `assets/` but is not in the load list. (verified)
- `themes/default.qss` defines `DEFAULT_STYLE` but nothing references it; 45 `setStyleSheet` calls across 12 files carry the real styling. (verified by grep)
- Napoleon docstring gate baseline is keyed on line numbers, so the gate reports about 206 false "new" violations and cannot be a pass/fail check (Backlog card).
- No CI configuration was found (no `.github/`); tests, ruff, mypy and the gate are run by hand per `AGENTS.md`. ^[inferred: other CI could exist outside the repo]
- The graphify snapshot is behind HEAD; `graphify update .` is AST-only and free.

## Packaging and portability

- macOS only today. Windows and Linux are Backlog cards. Portability debts already visible: the font-name case mismatch above; Linux user data in `~/.config` rather than the XDG data directory (Qt's `AppDataLocation` is `~/.local/share/<app>` and is meant for persistent app data); `QSystemTrayIcon` behaviour; the macOS help book path.
- "Check for updates" is a Backlog card gated on packaging.

## Suggested order if the goal is performance and responsiveness

1. Measure: a synthetic 500-sentence section, cold start, section switch, PDF export time. (Nothing here is measured yet.)
2. P3 (drop per-render refresh) and P4 (debounce/merge ModE edits): small, local, high leverage.
3. P1 (worker + progress for PDF/DOCX/import/backup), because it removes beach-ball freezes.
4. P2 (virtualize sentence cards) only if step 1 shows load time is the problem.

## Sources

Repo files and line numbers in the table; Trello cards F1 to F13 and On Deck bug cards.
