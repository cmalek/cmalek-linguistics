---
title: >-
    Morphology generation
category: concepts
tags: [old-english, morphology, python, wyrdcraeft]
relationships:
  - target: "[[projects/wyrdcraeft/wyrdcraeft]]"
    type: part_of
  - target: "[[concepts/old-english-grammar]]"
    type: related_to
  - target: "[[projects/wyrdcraeft/concepts/dictionary-build]]"
    type: part_of
  - target: "[[projects/wyrdcraeft/concepts/wright-catalog]]"
    type: uses
  - target: "[[projects/wyrdcraeft/concepts/dictionary-query-and-browse]]"
    type: precedes
  - target: "[[synthesis/Research: Old English Morphology Generation]]"
    type: related_to
  - target: "[[concepts/old-english-form-generation]]"
    type: related_to
  - target: "[[skills/using-nerthus]]"
    type: related_to
  - target: "[[skills/using-doec]]"
    type: related_to
sources:
  - "repo:github.com/cmalek/wyrdcraeft"
summary: >-
    Inside dictionary build, generation loads lemmas, assigns paradigms and Wright classes, then writes inflected forms to SQLite.
provenance:
  extracted: 0.85
  inferred: 0.12
  ambiguous: 0.03
base_confidence: 0.59
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T16:50:00Z
updated: 2026-10-12T04:37:00Z
---

# Morphology generation

Generation is a stage of [[projects/wyrdcraeft/concepts/dictionary-build]], not its own `morphology build` command. It reads bundled files under `wyrdcraeft/etc/morphology` (dictionary TSV, manual forms, verbal paradigms, prefixes). Overrides are `--data-dir`, `--dictionary`, `--manual-forms`, `--verbal-paradigms`, and `--prefixes`.

The default artifact is rows in `forms` inside `wyrdcraeft.sqlite3`. Pass `--output` to also write a TSV. `--profile` prints stage and SQLite flush timings. `--refresh-catalog` reloads `wright_paradigms.json`. `--limit` caps a non-full run. R-stem nouns stay off unless enabled.

Correctness is judged against the grammar references in the repo, not against the old Perl generator.

## Flow

```mermaid
flowchart TD
    start[Generation requested] --> load[Load dictionary, manuals, paradigms, prefixes]
    load --> limit[Apply full or limit]
    limit --> norm[Strip prefixes and hyphens, count syllables]
    norm --> paradigms[Assign verb, adjective, then noun paradigms]
    paradigms --> refs[Seed parts of speech and inflection codes]
    refs --> catalog[Seed Wright catalog unless already present]
    catalog --> classes[Assign lemma morph classes]
    classes --> stages[Generate forms]
    stages --> sqlite[(forms in SQLite)]
    stages --> tsv[Optional TSV when --output is set]

    stages --> manual[Manual forms]
    manual --> verbs[Verbs]
    verbs --> adjs[Adjectives]
    adjs --> advs[Adverbs]
    advs --> nums[Numerals]
    nums --> nouns[Nouns]
```

Lemma class assignment runs on dictionary-loaded lemmas before generation. Participles that verb generation later adds to the adjective pool are not assigned in that same run.

Verb generators are engines, not Wright conjugation classes. Strong is ablaut. Weak covers Weak I/II derivation, and item shape covers Weak III, preterite-present, and anomalous. Manual forms run first, as their own stage.

`wyrdcraeft morphology query --db PATH` reads generated rows from a SQLite file. `wyrdcraeft morphology clean-dictionary` backs up the morphology source TSV, fixes long diphthongs in column 2, lowercases all-uppercase titles, and drops duplicate rows.

`dictionary generate-reference-snapshots` writes compressed Python-reference snapshots, by default under `tests/python_reference/data`. That is a test artifact, not the app database.

## Scholarship

The design matches [[references/tichy-2017-morphological-analyser|Tichý 2017]]: a closed lemma list, class assignment, then paradigm expansion. His measured recall is 95 percent on 2,554 words of mostly late West Saxon prose, and he deliberately does not emit a dialect label on every cell or inflect compounds that are not already headwords. [[synthesis/Research: Old English Morphology Generation]] collects the later resources (Nerthus class fields, PaVeDa case frames, DOE attested spellings) that sit outside this stage. Class for a headword already in Nerthus is looked up in the guest database; the steps are [[skills/using-nerthus]]. Whether a generated spelling is attested is a separate search of the Dictionary of Old English Web Corpus ([[skills/using-doec]]). The corpus is not redistributed with this project.
