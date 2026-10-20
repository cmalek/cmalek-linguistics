---
title: >-
  aenglisc_toolkit: what it does now (v1.1.0)
category: concepts
tags: [aenglisc-toolkit, old-english, features, pyside6]
relationships:
  - target: "[[projects/aenglisc-toolkit/aenglisc-toolkit]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-intent]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-architecture]]"
    type: related_to
sources:
  - "repo:/Users/cmalek/src/personal/aenglisc_toolkit @ 981e093 (v1.1.0)"
  - "repo: CONTEXT.md, README.md, oeapp/help/topics/*.md, doc/source/overview/*.rst"
summary: >-
  Feature inventory of aenglisc_toolkit 1.1.0: a hierarchical OE text editor with per-token and idiom annotation, notes, remembered annotations and presets, search with layered highlighting, a full-translation view, PDF/DOCX/JSON/text export, and backup/migration safety.
provenance:
  extracted: 0.85
  inferred: 0.15
  ambiguous: 0.0
base_confidence: 0.55
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T20:05:00Z
updated: 2026-10-18T20:05:00Z
---

# aenglisc_toolkit: what it does now (v1.1.0)

Snapshot of repo HEAD `981e093` ("Bump version: 1.0.1 to 1.1.0"). PySide6 on Python 3.13+, SQLite via SQLAlchemy 2 and Alembic, about 40k lines in `oeapp/` (including migrations), about 1,080 test functions. Intent is in [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-intent]]; structure is in [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-architecture]].

## Text model

Project > Chapter > Section > Paragraph > Sentence > Token, with Idioms (contiguous multi-token spans) and Notes (attached to a token, a span, or a sentence). Poetry is handled with *Verse Line* numbers on sentences. Text is imported or appended (`.txt`, `.xml`, `.tei`, `.md`) and tokenized, including hyphen merging. Hierarchy edits (split/merge paragraph, section, chapter, sentences) are undoable commands.

## Annotation

- Per-token and per-idiom annotation: POS (noun, verb, adjective, pronoun, determiner/article, adverb, conjunction, preposition, interjection) plus POS-specific fields (case, number, gender, declension, verb class and form, pronoun type, preposition-governed case, transitivity, requires-infinitive, impersonal, and others), root, Modern English meaning, contextual *Sense*, confidence 0-100, TODO marker.
- Fields are defined once in a UI-only `PosFieldCatalog` (ADR 0005) shared by the annotation modal, preset dialog and details sidebar.
- **Annotation presets**: named bundles applied manually while filling the form (noun, verb, adjective, pronoun, determiner only).
- **Remembered annotations**: token-level templates keyed on exact surface, global or per-project (project wins), batch-applied; a propagation service also copies an annotation to matching tokens.
- **Copied Annotation**: in-session copy/paste of one token's annotation, validated through the `AnnotationJson` Pydantic schema (ADR 0006).
- Keyboard-driven: arrow keys move between tokens, `A` opens the modal, single letters pick POS inside the modal.

## Reading and review

- **Sentence cards** in a scroll area: read-only Old English with note superscripts and idiom italics, a Modern English editor, a notes panel, and a toggleable token table.
- **Token details sidebar** (right-hand splitter pane) for the selected token or idiom.
- **Highlighting modes** per sentence: none, POS, case, number, idiom. Three named layers (mode, span, search) are composed by the editor (ADR 0004); search always draws on top.
- **Search** across OE and Modern English with next/previous match and scope selector.
- **Full Translation window**: side-by-side whole-project OE and Modern English, with notes and its own highlighting.
- Chapter and section combo boxes navigate the hierarchy; one section is shown at a time.
- Light and dark themes via `qt_themes` (Nord and a modern light theme); bundled fonts (Maranatha, Anvers).
- In-app **Help Center** (QtHelp) and a macOS help book; a log viewer dialog.

## Export and transfer

| Output | Notes |
|---|---|
| PDF | LaTeX compiled by bundled Tectonic; side-by-side, footnotes, auto-built glossary |
| DOCX | python-docx |
| Project JSON (optionally gzip) | full project; Pydantic schema with `extra=forbid`; import creates a new project |
| Old English text / Translation text | reading copies with official titles and a verse number every five lines (ADR 0003) |

## Safety

- Autosave with 500 ms debounce; undo/redo stack of 50 commands.
- Automatic backups (default every 12 hours, 5 kept, checked every 5 minutes), manual backups, Restore dialog.
- Alembic migrations run at startup with a pre-migration backup and automatic restore on failure; databases from newer builds are refused with a dialog naming the version to install (ADR 0007).
- Fresh databases are built from the models and stamped at head rather than replaying revisions (the revision chain cannot replay from empty; see [[projects/aenglisc-toolkit/skills/alembic-migration-service]]).

## Platform and packaging

macOS only today: PyInstaller spec and `build_macos.sh`/`.dmg`. A `build_windows.bat` exists but Windows and Linux builds are Backlog cards. Tectonic binaries and a TeX bundle are shipped under `assets/tectonic`.

## Known defects on the board

On Deck bugs (remembered annotations skip capitalized and line-initial words; paste is not undoable; search does not scroll to the first match; context menu fails on line-initial words) and Backlog bugs (note on an idiom; Enter and arrow keys on idioms; J/K navigation). See [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-roadmap-trello]].

## Sources

Repo files named in the front matter; Trello board read 2026-10-18.
