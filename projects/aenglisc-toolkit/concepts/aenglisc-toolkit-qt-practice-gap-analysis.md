---
title: >-
  aenglisc_toolkit: Qt practice gap analysis
category: concepts
tags: [aenglisc-toolkit, qt, pyside6, best-practice, design]
relationships:
  - target: "[[projects/aenglisc-toolkit/aenglisc-toolkit]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/qt-app-design-references]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-internal-improvements]]"
    type: related_to
  - target: "[[references/fincept-terminal-qt-architecture]]"
    type: related_to
sources:
  - "repo:/Users/cmalek/src/personal/aenglisc_toolkit @ 981e093 (grep counts, 2026-10-18)"
  - "url:https://doc.qt.io/qt-6/qundostack.html"
  - "url:https://doc.qt.io/qt-6/qthreadpool.html"
  - "url:https://doc.qt.io/qt-6/qmainwindow.html"
  - "url:https://doc.qt.io/qt-6/model-view-programming.html"
  - "url:https://doc.qt.io/qt-6/internationalization.html"
  - "url:https://doc.qt.io/qt-6/qstandardpaths.html"
summary: >-
  Baseline of which stock Qt facilities aenglisc_toolkit uses and which it reimplements or skips (QUndoStack, worker threads, saved window state, delegates, proxy models, QStandardPaths, i18n, single-instance lock), with a candidate list of what to study in the seven reference apps.
provenance:
  extracted: 0.60
  inferred: 0.40
  ambiguous: 0.0
base_confidence: 0.45
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T20:25:00Z
updated: 2026-10-18T20:25:00Z
---

# aenglisc_toolkit: Qt practice gap analysis

Purpose: a baseline for deciding where to apply Qt patterns from other codebases. Written for an author who has built desktop apps before but not in Qt, so the entries explain the Qt facility as well as the gap.

Method and limits: counts come from `grep -E` over `oeapp/**/*.py` excluding Alembic, on 2026-10-18. Zero hits mean "not used in that form", not "no equivalent". The Qt facts come from the official Qt 6 documentation pages listed in the front matter. Context7 was requested for this research but its tools were not available in the session, so Qt for Python (PySide6) API names should be rechecked against the PySide6 docs when implementing. Nothing here was profiled.

## Baseline: what the app already does well

- `AppContext(QObject)` with signals for shared state; `QSettings` for preferences (28 hits in 10 files).
- A real `QAbstractTableModel` for the token table (`TokenTableModel`) rather than a `QTableWidget`.
- `QHelpEngine`-based help with contents, index and search ([[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-documentation-audit]]).
- Palette-driven themes via `qt_themes` applied at runtime, with a palette-based `QSplitter` sidebar style.
- Debounced autosave and a deferred first-show dialog with `QTimer.singleShot`.
- A compositor for `QTextEdit.ExtraSelection` layers (ADR 0004).
- `QSplitter` with `setChildrenCollapsible(False)` and a recorded reason.
- Selective use of `QKeySequence.StandardKey` (4 hits).

## Gap table

| Qt facility | What Qt provides | In this app | Gap and likely payoff |
|---|---|---|---|
| **`QUndoStack` / `QUndoCommand`** | Stack with `push`, `setClean`/`cleanChanged`, `beginMacro`/`endMacro`, merge by `id()` + `mergeWith()`, `undoLimit`, `createUndoAction`/`createRedoAction` (text follows the command), `QUndoView`, `QUndoGroup` | 0 hits. Hand-built `Command` ABC and `CommandManager` with two lists, cap 50, no merge, no macros, no clean state | Medium to high. Merging fixes the per-keystroke ModE problem ([[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-internal-improvements]] P4); macros make multi-step actions (paste annotation plus propagate; hierarchy changes) one undo; Edit menu items would read "Undo Edit Sentence". Commands already persist to the DB, so wrap them as `QUndoCommand` subclasses rather than redesign. |
| **Worker threads** (`QThreadPool` + `QRunnable`, `QProcess`, Qt Concurrent) | Pool manages threads; the Qt page says `QThreadPool` is thread-safe and low level; progress reporting is not covered there, so use signals from a `QObject` helper | 0 hits for any threading class. PDF, DOCX, import/export, ingest and backups block the UI | High for responsiveness. Needs a design for the single SQLAlchemy session: workers must not touch the UI thread's session (see Trello F8). Tectonic is an external process, so `QProcess` avoids the problem. |
| **`QMainWindow` state** | `saveGeometry`/`restoreGeometry`, `saveState`/`restoreState(version)`, toolbars and docks with `objectName`, `QStatusBar` | 0 hits for save/restore. Window opens at fixed `(100, 100, 1600, 800)`; splitter sizes fixed; no `QToolBar` or `QDockWidget` (toolbars are hand-built `QWidget`s) | Medium, cheap. Persist geometry and splitter state in `QSettings` at close and restore at launch. Moving the details sidebar into a `QDockWidget` gives floating, tabbed and hide/show for free (and the "no View-menu toggle to bring it back" comment in `main_window.py` disappears). |
| **Real `QToolBar` + `QAction`** | Actions carry text, icon, shortcut, tooltip, status tip and enabled state; reused in menus and toolbars | `QAction` is used in `menus.py` (24 hits). The top toolbar and navigation toolbar are custom `QWidget`s; bare-letter `QShortcut`s are registered on the window | Medium. One action object per command removes the duplicated enable/disable logic (Trello F1 notes export eligibility is gated on `QAction.isEnabled()`), and lets the help table be generated. Prefer `QKeySequence.StandardKey` for Undo/Redo/Find so macOS gets platform keys; Redo currently is `Ctrl+R`. |
| **Model/view for lists** | One model feeds many views; use `QStyledItemDelegate` for custom painting and editing; proxy models transform or sort/filter | `TokenTableModel` yes. `QTableWidget/QListWidget/QTreeWidget` in 7 files (44 hits); 0 delegates; 0 `QSortFilterProxyModel`; 0 `QCompleter` | Medium. Dialog lists (backups, presets, remembered annotations, log viewer, open project) could share models and proxies for filter-as-you-type. A delegate could paint the sentence read view and replace widgets-per-sentence ([[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-internal-improvements]] P2). |
| **Standard paths** | `QStandardPaths.AppDataLocation` for persistent app data (`~/Library/Application Support/<app>` on macOS, `~/.local/share/<app>` on Linux, `AppData/Roaming` on Windows; `AppLocalDataLocation` is the Windows local path) | 0 hits. Custom `get_app_data_path()` puts Linux data in `~/.config` | Low now, matters at the Linux build. Switch to `QStandardPaths`, keep the `AENGLISC_TOOLKIT_DATA_PATH` override, and migrate an existing folder. |
| **Internationalization** | `tr()`, `lupdate`/`lrelease`, `QTranslator`, `QLocale` | 1 hit. All UI strings are literals | Low priority for a one-user scholarly tool, but the Start Here page promises translation "into your own language"; if UI localisation ever matters, wrapping strings is cheaper early than late. |
| **Single instance** | `QLockFile`, `QSharedMemory` | 0 hits | Small, safe win; troubleshooting already warns about two instances. |
| **Progress and feedback** | `QProgressDialog`, `QStatusBar`, notifications | 0 progress widgets; status bar via one helper; a `QSystemTrayIcon` welcome balloon on every launch | Pair with worker threads; drop the tray message. |
| **Styling** | Palette first, `QSS` sparingly; Qt-only SASS via qtsass in one reference app | 45 `setStyleSheet` calls in 12 files plus an unreferenced `default.qss` | Medium. Consolidate styles into one theme module so a theme switch (`refresh_theme_colors`) does not depend on per-widget strings. |
| **Accessibility** | Accessible names and descriptions, tab order, no colour-only meaning | 4 accessible-name hits in 1 file. Colour-coded POS/case highlighting | Medium. Highlight modes should also be readable without colour (underline styles, a legend). |
| **Help integration** | Context help with `QWhatsThis`, tooltips, status tips; help topic per dialog | Help Center exists; 0 `setWhatsThis`, 6 tooltips | See [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-documentation-audit]]. |
| **Qt Designer / `.ui` files, QML** | Declarative layouts | None; all layouts are code | Not recommended to change. A widgets app with a 1,500-line window is better helped by splitting classes than by a new UI technology. |
| **`qtpy`** | Qt abstraction layer | Declared in `pyproject.toml`; only `ui/highlighting.py` imports it, everything else imports PySide6 directly | Low. Either import PySide6 there and drop the dependency, or accept one stray abstraction layer. |

## What to look at in each reference app

These map the seven clipped apps ([[projects/aenglisc-toolkit/concepts/qt-app-design-references]]) to the gaps above. The references were summarised from README clippings only, not from their source, so each row is a place to look, not a finding. ^[inferred]

| Reference | Look for |
|---|---|
| [[projects/aenglisc-toolkit/references/qutebrowser]] | Python/PyQt structure at scale: commands as first-class objects, keyboard-first input, config and settings handling, a built-in `:help` and `:report`; closest match for shortcuts, command objects and bug-report flow |
| [[projects/aenglisc-toolkit/references/letos]] | Mature C++/Qt SQLite front end: model/view for result grids, dock-based layout, SQL editor, undo, plugin boundaries |
| [[projects/aenglisc-toolkit/references/musescore]] | WYSIWYG editor with a large undo model, selection model, palette/inspector panels (comparable to the details sidebar), and open interchange formats |
| [[projects/aenglisc-toolkit/references/qtexamples]] | Idiomatic PySide patterns for threads, model/view, delegates and drag-and-drop, as small runnable code |
| [[projects/aenglisc-toolkit/references/qtsass]] | Centralised stylesheet source and variables for a theme layer |
| [[projects/aenglisc-toolkit/references/serial-studio]] | A declarative project file driving the UI; worker/IO separation from the dashboard; relevant to presets and POS field catalog as data |
| [[projects/aenglisc-toolkit/references/qtranslate]] | Select-then-lookup flow and plugin boundary for external dictionaries, relevant to the Bosworth-Toller and Wiktionary lookup cards and a future dictionary |
| [[references/fincept-terminal-qt-architecture]] | Already compared: ExtraSelection ownership, worker threads, and screen/state lifecycle |

## Suggested order of study (for discussion)

1. Threads and progress (qtexamples, qutebrowser) because it is the largest verified gap.
2. `QUndoStack` with merge and macros (musescore, Qt docs) because it fixes a verified data-loss-adjacent behaviour.
3. Window state, actions and docks (letos, qutebrowser).
4. Model/view for dialogs, then a delegate-based read view (qtexamples, letos) if profiling points there.
5. Style consolidation and accessibility (qtsass).

## Sources

Qt 6 pages listed in the front matter (QUndoStack, QThreadPool, QMainWindow, Model/View Programming, Internationalization, QStandardPaths). The Model/View page was only read to about 100,000 of 139,925 characters; the proxy-model and virtualization sections were not confirmed there, so those two points rest on general Qt knowledge. ^[inferred]

## Related

- [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-idiom-plan]] — the gaps rechecked against the official Qt docs
