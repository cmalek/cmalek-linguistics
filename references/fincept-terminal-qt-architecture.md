---
title: >-
  FinceptTerminal: Qt architecture lessons for aenglisc_toolkit
category: references
tags: [qt, architecture, desktop-app, pyside]
relationships:
  - target: "[[projects/aenglisc-toolkit/aenglisc-toolkit]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/skills/qt-extraselection-highlight-layers]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/skills/alembic-migration-service]]"
    type: related_to
sources:
  - "repo:github.com/Fincept-Corporation/FinceptTerminal"
source_url: "https://github.com/Fincept-Corporation/FinceptTerminal"
summary: >-
  What a C++20/Qt 6.8 finance terminal does well and badly, read as a source of patterns for a PySide annotation app, with each pattern checked against aenglisc_toolkit's code.
provenance:
  extracted: 0.67
  inferred: 0.28
  ambiguous: 0.05
base_confidence: 0.4
lifecycle: draft
lifecycle_changed: "2026-10-15"
tier: supporting
created: 2026-10-15T00:00:00Z
updated: "2026-10-18T19:48:28.152600+00:00"
snapshots:
  - "[[_raw/_archived/GITHUB FinceptTerminal 2026-10-15|GITHUB FinceptTerminal 2026-10-15]]"
  - "[[_raw/_archived/GITHUB FinceptTerminal 2026-10-15-1|GITHUB FinceptTerminal 2026-10-15-1]]"
---

# FinceptTerminal: Qt architecture lessons for aenglisc_toolkit

FinceptTerminal is a finance product with no linguistics content, so it is useful here only as a large, real Qt codebase (roughly 1,000 `.cpp` files under `fincept-qt/`, AGPL-3.0 plus a commercial licence, so read it, don't copy it). The review was a skim: nothing was built or run, and not every module was read. Claims about [[projects/aenglisc-toolkit/aenglisc-toolkit]] were checked against `oeapp/` by grep on 2026-10-15 unless marked unverified.

## Architecture in brief

- **Boot:** `app/main.cpp` takes a single-instance lock, opens the DB, shows a blocking dialog and exits on a fatal migration error, sets the theme, then starts the session.
- **Screens:** `DockScreenRouter` registers factories and builds a screen on first navigation. `IStatefulScreen` gives `save_state`, `restore_state`, `state_version`; `ScreenStateManager` writes that to SQLite with a 500 ms debounce.
- **Data:** `DataHub` is a topic pub/sub with a last-known-good cache and per-topic policy (TTL, coalescing). Storage is SQLite with integer-versioned migrations that self-register (`MigrationRunner`).
- **Theme:** `ThemeTokens` struct, `ThemeManager` builds one QSS string and emits `theme_changed(tokens)`.
- **Background work:** `PythonRunner` (per-call `QProcess`, timeout, max 3) and `PythonWorker` (long-lived daemon, length-prefixed JSON, per-request deadlines, restart on death).
- **Actions:** `ActionDef` and `ActionRegistry` drive menus, palette, and rebindable hotkeys from one definition.
- **Errors:** `Result<T>` for expected failures; tagged migration errors decide whether to boot.

## Patterns worth taking

| Pattern | Fincept | aenglisc_toolkit today |
|---|---|---|
| Single owner of a contested resource | `ThemeManager` is the only `setStyleSheet` writer | `ui/highlight_layers.py` exists and is used in `oe_text_edit.py`, but `setExtraSelections` is still called directly at about 10 sites in `highlighting.py` and `full_translation_window.py`. The vault note [[projects/aenglisc-toolkit/skills/qt-extraselection-highlight-layers]] says "not implemented"; the repo is further along. |
| Fatal boot gate on bad migration | tagged error, dialog, exit before the window exists, `.pre-vN.bak` first | `services/migration.py` already has backup, rollback, `MigrationFailed`, `UnknownDatabaseRevision`. Whether the empty-DB `create_all` + stamp path goes through the same gate is unverified. |
| Versioned, debounced UI state | `IStatefulScreen` plus state store | No geometry or splitter persistence found; `services/autosave.py` has a debounce to reuse. |
| Long work off the UI thread, with deadlines | `PythonRunner` / `PythonWorker` | No `QThread`, `QRunnable`, or thread pool found. PDF export (`export_pdf.py`, 1,522 lines), wyrdcraeft ingest, docx export, and backup appear to run on the UI thread (not each confirmed). |
| One action definition for menus, palette, hotkeys | `ActionRegistry` | `ui/menus.py` and `ui/shortcuts.py` are separate; `services/keymap.py` is effectively empty. |
| Theme tokens plus a signal | `ThemeTokens`, `theme_changed` | `ui/theming.py` only sets a palette theme; whether highlight colours follow a live switch is unverified. |

Also noted: `services/autosave.py` prints exceptions and clears `_pending`, so a failed autosave is silently dropped. A signal surfaced in the main window would fix that.

## Not worth copying

- **Docs overstate code.** `ARCHITECTURE.md` names QCoro as preferred, but there are zero QCoro uses; its ADR index lists seven ADRs that do not exist in `docs/adr/`; its "SQL in background" rule is contradicted by dozens of screens calling the DB directly.
- **Newer-schema refusal is documented, not implemented.** The tag is declared but never produced, and `main.cpp` says the case "warns and returns ok". aenglisc_toolkit's `UnknownDatabaseRevision` is the better version.
- **`ThemeManager` is a stub** (ignores its argument, always applies one theme) and about 4,100 `setStyleSheet` calls bypass the tokens.
- **Overbuilt for a single-user annotation app:** `DataHub` (a singleton with string topics, meant for sharing broker fetches), multi-window docking and tear-off, `InstanceLock`, secure storage, MCP and agent layers, `X::instance()` singletons. The explicit `AppContext` in `state.py` is better for tests.
- **Tests are thin** (four Qt Test suites); aenglisc_toolkit is already ahead. Only the headless `--selftest-*` flag idea is worth a look.

## First experiments, in order

1. Finish the compositor and add a test that fails if any file but `highlight_layers.py` calls `setExtraSelections`.
2. Run PDF export on a `QRunnable` with `progress`, `failed`, `finished` signals and a cancel `Event`.
3. Add a boot error gate; try folding the empty-DB path into it.
4. Add a `ViewStateStore` for geometry, splitters, and last chapter.
5. Make autosave failures visible and retryable.
6. Spike an `Action` registry for 5–10 menu items and a small palette.

## Revised README snapshot and temporal limits

The revised clip describes a C++20/Qt 6 application with embedded Python and pins its build instructions to Qt 6.8.3, Python 3.11.9, CMake 3.27.7, and Ninja 1.11.1. It says public development has moved to monthly releases while daily work focuses on Enterprise. These are claims of the captured README, not a fresh build or repository audit.

The older introduction’s “commercial licence” wording needs a qualification: this snapshot says a separate commercial or academic licence for the public repository is no longer sold and describes Enterprise as a separate product. It does not change the recorded AGPL label for the public repository. The architecture observations above remain dated to their original code review; this clipping does not revalidate them.

## Sources

- [[_raw/_archived/GITHUB FinceptTerminal 2026-10-15]]
- Repo and `/Users/cmalek/src/personal/aenglisc_toolkit` read directly on 2026-10-15 (read-only, nothing executed).
- [[_raw/_archived/GITHUB FinceptTerminal 2026-10-15-1.md]]
