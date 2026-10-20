---
title: >-
  aenglisc_toolkit: Trello board snapshot (2026-10-18)
category: concepts
tags: [aenglisc-toolkit, roadmap, trello, planning]
relationships:
  - target: "[[projects/aenglisc-toolkit/aenglisc-toolkit]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-intent]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-internal-improvements]]"
    type: related_to
sources:
  - "url:https://trello.com/b/lEVKtPBa/aenglisc-toolkit"
summary: >-
  Snapshot of the 52 cards on the Aenglisc Toolkit Trello board by list: 1 Doing, 6 On Deck, 29 Backlog (unordered), 3 Phase Infinity (someday), 13 Released (possibly including older releases); the F1-F12 architecture audit is the structured backbone.
provenance:
  extracted: 0.90
  inferred: 0.10
  ambiguous: 0.0
base_confidence: 0.55
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T20:30:00Z
updated: 2026-10-18T20:30:00Z
---

# aenglisc_toolkit: Trello board snapshot (2026-10-18)

Board: *Ænglisc Toolkit* (`lEVKtPBa`), read through the Trello API on 2026-10-18. List meanings (stated by the user): **Phase Infinity** = someday, not important now; **Backlog** = wanted, in no particular order; **On Deck** = next; **Doing** = in progress or imminent; **Released** = finished, kept until a release is packaged, and not always cleared promptly. The `Reference` list is empty.

Card counts: Doing 1, On Deck 6, Backlog 29, Phase Infinity 3, Released 13.

## Doing

- **F6** MigrationService mixes Alembic, a version catalog and a second backup path. Mostly resolved by ADR 0007 and the commits at HEAD (BackupService is the sole backup path; unknown-revision refusal; restore hardening). The card is still open, so remaining scope is the open questions: empty-DB policy (`create_all` + stamp vs replay), comparing revisions through the Alembic script graph instead of hex ordering, and deleting the unused `BackupFileMetadataService`. ^[inferred from git log vs card text]

## On Deck (next)

Six bug and data-integrity cards, all reproducible:

1. Pasting an annotation cannot be undone.
2. Audit and repair stale CHECK constraints on `annotations` and `remembered_annotations` (live DB has 1 of about 20 declared checks; also drops `'f'` from `verb_aspect`).
3. Words at the beginning of a line cannot be copied or remembered/propagated through the context menu.
4. Capitalized words do not receive remembered annotations (example *Hē*).
5. Search does not scroll to the first match; pressing `N` is required.
6. Words at the beginning of a line (example *Hī*) are skipped when applying remembered annotations.

Cards 3, 4 and 6 look like one root cause in matching on exact surface (see [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-internal-improvements]]). ^[inferred]

## Backlog (wanted, unordered)

| Group | Cards |
|---|---|
| Architecture audit (resolve order from cards) | F1 MainWindowActions god façade (8/12); F7 SentenceCard controller split (9/12); F8 process-global SQLAlchemy session (10/12); F9 FullTranslationPDFExporter god service (11/12); F10 coverage and test ownership (12/12); F13 ADR location and format |
| Bugs | note on an idiom does nothing; Enter on a selected idiom should open the annotation modal; arrow keys should select an idiom as a unit; `J`/`K` sentence navigation does nothing; napoleon-gate baseline is keyed on line numbers |
| Features: reading and display | several view modes (all, paragraph, section, chapter); Full Translation window updates live as the main window changes; global POS overlay and a per-word annotation dialog in the Full Translation window; alliteration overlay per Old English poetic rules |
| Features: annotation and dictionary | link words to antecedents; user-built dictionary; dictionary maintenance (choose main entry, verify, export to Wyrdcraeft); pure dictionary export (PDF, JSON); show normal endings and strong-verb vowel progression for a selected verb; add "Person" to personal pronouns; Wiktionary button beside Bosworth-Toller |
| Features: app and project | multiple projects open at once; edit chapter and section titles in Edit Project; "Check for updates" (after packaging works) |
| Packaging | Windows build; Linux build |
| Documentation | warn that remembered annotations match spelling only (examples *hild*, *þā*, *þæs*, *hearde*) |
| Refactoring | dialogs have huge, poorly named methods |

## Phase Infinity (someday)

Write a developer's guide; sentence diagramming mode; Modern English to Old English mode.

## Released (13; may include older releases)

F4 remove the conflicting `docx` 0.2.4 dependency; F5 prune unused runtime and test dependencies; F3 compositor for ExtraSelection layers (ADR 0004); F11 `SearchHighlighter` clear on read-only editors; F2 one POS field catalog (ADR 0005); F12 typed Copied Annotation (ADR 0006); audit cards "Note FK sanitization off autosave", "finish SentenceCard controller split, stop widget ORM writes", "unblock the suite (fix 6 failing tests)"; test coverage 90%; "known words with annotations you can instantly apply" (remembered annotations); "include all notes in the help system"; "stop building help on every startup". Because the Released list is not strictly cleared per release, treat it as "done", not "shipped in 1.1.0".

## About the audit (F1-F13)

The F-cards come from an architecture and capability audit (reports dated 2026-09-01 and 2026-09-13, saved to `/tmp` and no longer in the repo). Each card is written as an agent briefing that asks for a `/grill-with-docs` session before code, with a recommended first answer, scope in and out, evidence and constraints. The card text itself is the best record of intent for these refactors.

## Gaps between the board and this research

- No card tracks background threads or progress feedback (P1 in [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-internal-improvements]]); F9 mentions it as optional.
- No card for the autosave silent-failure path, a single-instance lock, window geometry persistence, or contextual help.
- No card for the keyboard-shortcut and help drift in [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-documentation-audit]] beyond the `J`/`K` bug.
- No card for performance measurement.

These are suggestions only; the user decides what becomes a card.

## Sources

Trello board API output (cards, lists, descriptions), 2026-10-18.
