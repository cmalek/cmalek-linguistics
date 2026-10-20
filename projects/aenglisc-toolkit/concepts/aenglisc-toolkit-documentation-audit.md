---
title: >-
  aenglisc_toolkit: documentation audit (global docs and in-app help)
category: concepts
tags: [aenglisc-toolkit, documentation, help-system, sphinx, qthelp]
relationships:
  - target: "[[projects/aenglisc-toolkit/aenglisc-toolkit]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-architecture]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-practice-gap-analysis]]"
    type: related_to
sources:
  - "repo:/Users/cmalek/src/personal/aenglisc_toolkit/doc/source"
  - "repo:/Users/cmalek/src/personal/aenglisc_toolkit/oeapp/help"
  - "url:https://trello.com/b/lEVKtPBa/aenglisc-toolkit"
summary: >-
  Two hand-maintained documentation sets (Sphinx on Read the Docs, QtHelp in the app) cover the same user topics with no shared source, and they already disagree with the code on shortcuts; there is no developer guide or API reference.
provenance:
  extracted: 0.75
  inferred: 0.25
  ambiguous: 0.0
base_confidence: 0.5
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T20:20:00Z
updated: 2026-10-18T20:20:00Z
---

# aenglisc_toolkit: documentation audit

## Inventory

**Global docs** (`doc/source`, Sphinx + `sphinx_rtd_theme`, published at aenglisc-toolkit.readthedocs.io): about 3,400 lines of RST in four groups.

- Getting Started: installation, quickstart, domain language (a rendering of `CONTEXT.md`).
- User guide: projects, project organization, annotation, presets, remembered annotations, translation, backups, updating, FAQ.
- Development: seven ADRs, contributing, coding standards, packaging.
- Reference: changelog.

Sphinx has `autodoc`, `napoleon` and `intersphinx` enabled, but the tree has no API reference pages, so docstrings (a Napoleon contract is enforced by a gate) are not published anywhere. Trello has "Write a developer's guide" in Phase Infinity.

**In-app help** (`oeapp/help`): 15 Markdown topics (about 8,700 words) in `help/topics/`, converted to HTML and compiled into a QtHelp collection (`.qch`/`.qhc`) at build time, plus a macOS help book. A `HelpEngine` wraps `QHelpEngine`; `HelpCenterDialog` shows contents, index, full-text search and a `QTextBrowser`, with a theme CSS override. Topics: Start Here, Settings, Keybindings, Annotation Guide, Remembered Annotations, Idioms, Incremental Annotation, Notes, Search, Full Translation Window, Export Formatting, Project Export/Import, Automatic Backups, Morphological Reference, Troubleshooting.

## What is good

- Both sets exist and are treated as deliverables; `AGENTS.md` requires in-app help for user-facing change.
- The help is a real Qt help system (contents, index, full-text search, `qthelp://` resources), built at build time, not at every startup (Trello Released card).
- The glossary (`CONTEXT.md`) is unusually disciplined and feeds the domain-language page.
- ADRs are written to a template; a backup and unknown-revision FAQ and in-app help shipped together with ADR 0007.

## Problems found

1. **Two sources of truth for user content.** Annotation, remembered annotations, backups, translation/Full Translation, export and project export/import each exist as both an RST page and a Markdown help topic, hand-written separately (about 7,200 words of RST overview vs about 8,750 of help; note not every page pairs one to one). Nothing generates one from the other, so they will drift.
2. **Documented behaviour already disagrees with the code.**
   - `keybindings.md` lists Redo as `Ctrl+Y` or `Ctrl+Shift+Z`; `ui/shortcuts.py` registers `Ctrl+R` and `Ctrl+Shift+R`, and no `Ctrl+Y` exists in `oeapp/ui`.
   - `keybindings.md` and `troubleshooting.md` say `J`/`K` navigate between sentences and work globally; no `J`/`K` binding exists in `oeapp/ui`, and a Backlog bug card reports it does nothing.
   - `GlobalShortcuts` lists `Ctrl+G`, `N`, `Shift+N`, `Shift+Up/Down`, none of which appear in the Keybindings topic, so the page is incomplete as well as wrong. ^[inferred: read of shortcuts.py against keybindings.md]
   - `troubleshooting.md` tells end users to "ensure `python-docx` is installed", which only makes sense for source installs.
   - The Keybindings topic mentions "Window > View Logs" and "F1"; confirm these against `menus.py` when fixing.
3. **No single place defines shortcuts.** Shortcuts are `QShortcut`s in `shortcuts.py`, `QAction` shortcuts in `menus.py`, and key handlers in widgets; the Help page is typed by hand. A table in code that both builds the bindings and generates the help table would remove the drift. ^[inferred]
4. **Help is not contextual.** Topics open from the Help menu (`show_help(topic=...)`), but there are no `Help` buttons in dialogs, `setWhatsThis` is not used anywhere (0 hits), `setToolTip` appears only 6 times, and `setStatusTip` never. Complex dialogs such as the Annotation Modal and Preset Management have no direct route to their topic.
5. **Known documentation debt on Trello.** Remembered annotations match on spelling only and can mis-apply (with *hild*, *þā*, *þæs*, *hearde* as examples) but this is not yet explained; the Backlog card asks for a prominent warning. Dictionary, pronoun person and other planned features have no doc stubs.
6. **No developer-facing map.** `AGENTS.md` and `CONTEXT.md` are written for coding agents; there is no architecture overview page, module map, or "how to add a POS field / migration / command" recipe in Sphinx. The graph report and ADRs carry that knowledge instead.
7. **Process drift.** Card F13: ADR location and format differ between `AGENTS.md` (RST under `doc/source/architecture/`) and some plans (`docs/adr/*.md`). The `docs/superpowers/plans/` folder holds eight implementation plans that are not published or indexed.
8. **Screenshots.** Only one screenshot (`screenshot-themes.png`) was seen in `doc/source/_static`; most user pages are text-only. ^[inferred: not exhaustively listed]
9. **Changelog is in Sphinx only.** Version 1.1.0 is tagged, but the in-app UI does not show release notes (no "What's new").

## Suggested improvements

1. **One source for user topics.** Make the Markdown help topics the source and render them into Sphinx (MyST include) or the reverse; keep a single sentence of difference only where behaviour really differs. Decide this once, then delete the duplicate prose.
2. **Generate the shortcut table from code.** Define bindings in one data structure (key, action id, description, scope) used by `GlobalShortcuts`, `menus.py` and the Keybindings topic build step. Add a test that fails when a documented shortcut is not registered.
3. **Fix the verified drift now:** Redo keys, J/K (either implement or remove from docs), the python-docx line, missing global shortcuts.
4. **Context help:** add a `Help` button (or `F1` handling) to each dialog that opens its topic via the existing `topic=` parameter; add tooltips and status tips to toolbar actions.
5. **Publish an API reference** with `sphinx-apidoc` or autosummary for `oeapp.models`, `services` and `commands`, since the docstring contract is already enforced.
6. **Write the developer guide** (Phase Infinity card) as an architecture overview using [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-architecture]] as the skeleton, plus three recipes: add a POS field (catalog + ORM + Alembic), add an undoable command, add a help topic.
7. **Add a docs check to the quality gate:** build Sphinx with `-W`, verify every help topic file is registered in `topics.py`, and check the `.qch` is newer than the topics.
8. **In-app discoverability:** a first-run tour or "What's new" topic fed from the changelog.
9. Reconcile the ADR location (F13) and index the `docs/superpowers/plans` folder or move it out of the repo's published docs.

## Sources

Repo `doc/source/**`, `oeapp/help/**`, `AGENTS.md`; Trello Backlog documentation cards; Qt help classes are shown on [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-practice-gap-analysis]].
