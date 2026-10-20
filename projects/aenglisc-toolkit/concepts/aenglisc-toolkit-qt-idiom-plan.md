---
title: >-
    aenglisc_toolkit: replacing hand-rolled code with stock Qt
category: concepts
tags: [aenglisc-toolkit, qt, pyside6, architecture, best-practice]
relationships:
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-practice-gap-analysis]]"
    type: extends
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-internal-improvements]]"
    type: related_to
  - target: "[[references/qt-official-docs-best-practice]]"
    type: derived_from
sources:
  - "[[references/qt-official-docs-best-practice]]"
  - "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-practice-gap-analysis]]"
  - "[[references/beginning-pyqt-willman-2022]]"
  - "repo:/Users/cmalek/src/personal/aenglisc_toolkit @ 981e093"
summary: >-
    The gap analysis rechecked against the official Qt pages: for each hand-built part, the stock facility, the doc warning that matters, and an order of work. Interprets "non-idiomatic/DIY" as hand-rolled code with a Qt equivalent.
provenance:
  extracted: 0.45
  inferred: 0.50
  ambiguous: 0.05
base_confidence: 0.55
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T22:30:00Z
updated: 2026-10-18T22:30:00Z
---

# aenglisc_toolkit: replacing hand-rolled code with stock Qt

The request said "non-idomatic/DIY as much as possible"; this page reads it as *remove non-idiomatic and hand-rolled code where Qt already ships the facility*. If it meant the opposite, only the framing changes. The gap table on [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-practice-gap-analysis]] listed what is missing; this page adds what the official documentation says about each, from [[references/qt-official-docs-best-practice]]. Nothing was profiled or implemented, and PySide6 names are checked only where that page says so.

## Ranked changes

| # | Hand-rolled today | Stock facility | What the docs add | Evidence in this repo |
|---|---|---|---|---|
| 1 | `Command` ABC and `CommandManager`, 50 cap, no merge | `QUndoStack` / `QUndoCommand` (`QtGui` in PySide6) | `undoLimit` defaults to unlimited; `mergeWith()` needs a matching non-negative `id()`; macros count as one command; `createUndoAction` names the next step; `setClean()` drives a modified marker | per-keystroke `EditSentenceCommand` evicts history (P4) |
| 2 | Blocking PDF/DOCX/import/backup on the GUI thread | `QProcess` for Tectonic; `QRunnable` plus a `QObject` signal helper for the rest | widgets are main-thread only; connect worker signals to `@Slot` methods, because a lambda "is executed in the sender's thread context"; give `QProcess` an absolute program path | P1; `subprocess.run` in `pdf_engine.py` |
| 3 | 45 `setStyleSheet` calls, string-built, themes via settings reads | one `.qss` file, palette roles, a `QPalette` per theme | "Don't assemble style sheets from C++ strings"; "Don't use this function to switch themes at runtime"; style sheets "win over programmatic settings" | gap analysis; P5 |
| 4 | Fixed window size, hand-built toolbars as `QWidget`s | `saveGeometry`/`saveState` with unique `objectName`s, `QToolBar`, `QDockWidget` | `restoreState(version)` fails safely on a layout change, so bump the version; Wayland does not report position | no save/restore found |
| 5 | Dialog lists in `QTableWidget`/`QListWidget` | `QSortFilterProxyModel` over a model, `QCompleter` | Qt recommends model/view "unless you strongly need an item-based set of classes" | 44 item-widget hits |
| 6 | One widget tree per sentence | `QListView` with a delegate, `uniformItemSizes` only if rows are equal, or lazy card creation | no page quantifies per-widget cost; measure first | P2, unmeasured |
| 7 | Second launch can open the same SQLite file | `QLockFile` in the data dir | use `setStaleLockTime(0)` and a short `tryLock`, then tell the user; stale detection can fail on network drives | troubleshooting page warns about it |
| 8 | Redo on `Ctrl+R`, bare-letter `QShortcut`s | `QKeySequence.StandardKey` on `QAction`s | `menuRole` and platform keys come from the standard keys | gap analysis |
| 9 | Custom `get_app_data_path()` | `QStandardPaths` | Linux `AppDataLocation` is `~/.local/share`, not `~/.config`; keep the env override | see [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-os-integration]] |

## Combining the undo stack with the text boxes

The Qt pages describe `QUndoStack` and the built-in `QTextDocument` history separately, with no sentence on combining them. Two workable options, both inferences: give the Modern English editor `setUndoRedoEnabled(False)` and push merged commands (merge key per sentence), or leave typing to the document and push a command only on focus-out. The second is closer to the Trello F7 suggestion. ^[inferred]

## Lessons from the book that still apply

[[skills/pyqt6-responsive-background-work]] shows the worker-and-signals shape, and its limits (`terminate`, no rollback) match the Qt pages' warning that `terminate()` is "dangerous and discouraged". Use `requestInterruption()` instead. [[skills/pyqt6-actions-and-main-windows]] already states the one-action-many-entry-points idea that item 8 depends on.

## Suggested order

1. Measure cold start, a 500-sentence section and export time (nothing is measured).
2. Items 1 and 2 (undo with merging, workers), the two verified defects.
3. Items 3, 4 and 8 together, since styles, window state and actions touch the same files.
4. Items 5 and 7 as small safe wins; item 6 only if step 1 says so.

## Not recommended

- Qt Designer `.ui` files or QML: the current Qt comparison says both technologies can build complex text editors, so switching buys nothing for a widgets app.
- A new framework layer such as a global event bus: [[references/fincept-terminal-qt-architecture]] already rated these as overbuilt for a single-user tool.

## Open Questions

- Does PySide6 keep Python-side references to a `QUndoCommand` after `push()`? Unconfirmed in the docs.
- Which `QUndoStack`-and-text-document combination feels right in use? Prototype both ([[skills/ux-prototyping]]).
- Is `pyside6-deploy` worth trying against the current PyInstaller build? See [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-os-integration]].

## Related

- [[projects/aenglisc-toolkit/aenglisc-toolkit]]
- [[synthesis/Research: Qt and Translation Workbench Best Practice]]

## Sources

- [[references/qt-official-docs-best-practice]]
- Repo findings on the linked baseline pages.
