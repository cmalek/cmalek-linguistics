---
title: >-
  unimorph/ang
category: references
tags: [old-english, morphology, dataset]
relationships:
  - target: "[[concepts/old-english-form-generation]]"
    type: related_to
  - target: "[[projects/wyrdcraeft/wyrdcraeft]]"
    type: related_to
sources:
  - "repo:github.com/unimorph/ang"
source_url: "https://github.com/unimorph/ang"
summary: >-
  A single 178k-row UniMorph file of Old English paradigms scraped from Wiktionary; the most directly usable resource among the GitHub repos reviewed, CC BY-SA.
provenance:
  extracted: 0.8
  inferred: 0.15
  ambiguous: 0.05
base_confidence: 0.5
lifecycle: draft
lifecycle_changed: "2026-10-15"
tier: supporting
created: 2026-10-15T00:00:00Z
updated: 2026-10-15T00:00:00Z
snapshots:
  - "[[_raw/_archived/GITHUB ang 2026-10-15|GITHUB ang 2026-10-15]]"
---

# unimorph/ang

The repo holds one data file, `ang` (6.7 MB, 178,373 lines), and no code. Each line is `lemma<TAB>form<TAB>features`, for example `beran	bireþ	V;IND;SG;3;PRS`. It was machine-extracted from English Wiktionary inflection tables.

## What is in it

| Part of speech | Lemmas (approx.) | Rows |
|---|---|---|
| Nouns | 3,500 | 30,500 |
| Adjectives | 1,400 | 102,000 |
| Verbs | 2,400 | 40,800 finite, 5,000 participle |

Features are standard UniMorph (NOM, ACC, GEN, DAT, INS, SG, PL, genders, PRS, PST, IND, SBJV, IMP, NFIN). Orthography is Wiktionary's, with macrons and dotted ġ/ċ. Variant forms are separate rows (`birst`, `birest`, `bireþ`).

## Cautions

- The README still has `XX`/`YY` placeholder counts and describes `LGSPEC1-3` as possessive and second-person-object tags. In the data, `LGSPEC01` and `LGSPEC02` sit on every adjective row, probably strong versus weak, but this is undocumented. ^[inferred]
- Some nouns carry no gender (`gōd`), nouns have no instrumental, and some forms are duplicated.
- No dialect tags; the data is West-Saxon-like.
- CC BY-SA 3.0 inherited from Wiktionary, so redistribution inside another repo carries share-alike terms.
- Single commit, last 2022-03-22, no tests.

## Use for wyrdcraeft

Good as a gold or evaluation set for a paradigm generator and as a form-to-(lemma, features) lookup. Verbs are the most complete. Normalise macrons and dotted consonants before matching against corpus text. See [[concepts/old-english-form-generation]] and [[projects/wyrdcraeft/concepts/morphology-generation]].

## Sources

- [[_raw/_archived/GITHUB ang 2026-10-15]]
- Repo read directly on 2026-10-15 (shallow clone, nothing executed).
