---
title: >-
  aenglisc_toolkit: intent and product principles
category: concepts
tags: [aenglisc-toolkit, old-english, product, design-intent]
relationships:
  - target: "[[projects/aenglisc-toolkit/aenglisc-toolkit]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-current-capabilities]]"
    type: related_to
  - target: "[[concepts/old-english]]"
    type: related_to
sources:
  - "repo:/Users/cmalek/src/personal/aenglisc_toolkit (README.md, CONTEXT.md, oeapp/help/topics/start-here.md)"
  - "url:https://trello.com/b/lEVKtPBa/aenglisc-toolkit"
summary: >-
  The app is a manual, translator-in-control workbench for Old English: it never auto-translates or auto-annotates, and every design choice (incremental annotation, remembered annotations, undo, backups) serves keeping a human's linguistic decisions organized.
provenance:
  extracted: 0.80
  inferred: 0.20
  ambiguous: 0.0
base_confidence: 0.55
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T20:00:00Z
updated: 2026-10-18T20:00:00Z
---

# aenglisc_toolkit: intent and product principles

## One-sentence intent

A local-first desktop workbench that keeps an Old English source text, the translator's morphological analysis, notes and Modern English translation in step with each other, while leaving every linguistic decision to the human.

`CONTEXT.md` in the repo states this directly: "The translator makes every linguistic decision; the app does not auto-translate or auto-annotate." The in-app *Start Here* page lists "What This App Is Not": not an automatic translator, no automatic morphological annotation, no disambiguation of grammar or meaning.

## Who it is for

- The author, a translator working on long texts (verse such as *The Seafarer* and *Maldon* appear in fixtures and Trello examples). ^[inferred]
- Students and scholars of [[concepts/old-english]]; the README says they "don't need software that guesses at grammar for you".
- Distribution is a macOS `.app`/`.dmg` today; Windows and Linux builds are Backlog cards. Other people's desktops are a real constraint (see the Alembic rule in [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-architecture]]).

## Product principles (extracted)

1. **The translator decides.** The glossary calls the human the *Translator* and forbids "annotator-as-bot". Remembered annotations carry an explicit worry on Trello: a list of known words could become "a nearly automatic translator". A Backlog card asks for documentation that remembered annotations match on spelling only (*hild* m. "battle" vs f. "safety"; *þā* adverb vs article).
2. **Incremental annotation.** Tag the POS now, refine later; a *TODO Marker* flags unfinished annotations.
3. **Preserve philological signal.** Surface spelling keeps case and diacritics; a separate *Normalized Form* (lowercase, diacritics stripped, `ð` folded to `þ`) is used only for grouping and search. The Sphinx index says "built for scholars first".
4. **Data safety over convenience.** Autosave (500 ms debounce), 50-deep undo, automatic and on-demand backups, a pre-migration backup with automatic restore, and an *Unknown Database Revision* check that refuses a database written by a newer build.
5. **Domain language is enforced.** `CONTEXT.md` defines ~50 terms with "_Avoid_" lists (Root not lemma, Surface not form, Copied Annotation not clipboard annotation).
6. **Fat models, thin UI.** `AGENTS.md` puts domain behaviour in the ORM and services, not widgets (see [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-architecture]]).
7. **Help is a first-class deliverable.** `AGENTS.md`: "We strongly enforce clear user-facing in app help." See [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-documentation-audit]].

## Longer-term ideas (not commitments)

On the Trello board, *Phase Infinity* means "someday, not important right now"; *Backlog* means wanted but unordered. See [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-roadmap-trello]].

- **Phase Infinity:** sentence-diagramming mode (needs word linking and clause marking first); a Modern English to Old English mode (annotating the target rather than the source); a developer's guide.
- **Backlog (wanted):** link words to antecedents with a display mode; a user-built authoritative dictionary with verified entries and export into [[projects/wyrdcraeft/wyrdcraeft]]; whole-document overlays in the Full Translation window to spot un-annotated words (they leave the glossary incomplete); an alliteration overlay following Old English poetic rules (needs sub-token IPA for `sc`, `ea`, `eo`).

## Tensions worth keeping in view

- *Manual by design* vs *remembered annotations and propagation*: a productivity feature that edges toward automation; docs and UI must keep the translator in the loop.
- *Scholar-grade fidelity* vs *desktop polish*: this is the author's first Qt app and they want to apply Qt best practice; see [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-practice-gap-analysis]].

## Sources

- Repo `README.md`, `CONTEXT.md`, `AGENTS.md`, `oeapp/help/topics/start-here.md`, `doc/source/index.rst`.
- Trello board *Ænglisc Toolkit* (52 cards read 2026-10-18); list meanings per the user.
