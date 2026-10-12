---
title: >-
  York-Toronto-Helsinki Parsed Corpus
category: entities
tags: [old-english, corpus, treebank]
aliases: [YCOE, YCOEP]
relationships:
  - target: "[[references/ycoe-case-and-pos-annotation]]"
    type: related_to
  - target: "[[concepts/old-english-lemmatisation]]"
    type: related_to
  - target: "[[entities/varioe]]"
    type: related_to
sources:
  - "url:https://www-users.york.ac.uk/~lang18/Documentation/pos-manual-oe.htm"
  - "url:https://aclanthology.org/2025.acl-srw.46.pdf"
summary: >-
  YCOE is 1.5 million words of parsed Old English prose. YCOEP is the poetry companion. Neither stores stem class.
provenance:
  extracted: 0.82
  inferred: 0.12
  ambiguous: 0.06
base_confidence: 0.70
lifecycle: draft
lifecycle_changed: 2026-10-09
tier: supporting
created: 2026-10-09T19:50:00Z
updated: 2026-10-09T19:50:00Z
---

# York-Toronto-Helsinki Parsed Corpus

The York-Toronto-Helsinki Parsed Corpus of Old English Prose (YCOE; Taylor, Warner, Pintzuk, and Beths, 2003) is the main syntactically annotated prose corpus. [[references/computational-study-of-old-english-2025|Martín Arista (2025)]] gives it as 1.5 million words with part-of-speech tags and phrase-structure trees. The poetry companion is the York-Helsinki Parsed Corpus of Old English Poetry (YCOEP; Pintzuk and Plug, 2001).

Tags are Penn-historical: category plus inflection (`N^D`, `VBPI`, `PRO^A`). The prose manual is [[references/ycoe-case-and-pos-annotation]]. [[references/miani-2025-oe-poetry-pos|Miani, Stymne, and Darwin (2025)]] count 289 prose tags and 201 poetry tags. Case is marked from the form, not from the governing verb.

The corpus was not lemmatised in the original release. [[entities/varioe|VARIOE]] added lemmas for the prose. The [[references/martin-arista-2026-oe-lemmatisation|2026 lemmatiser]] trains on prose and poetry triples extracted from these trees. [[entities/paveda|PaVeDa]] samples them for valency.

YCOE is the wrong place to read noun class or a complete government lexicon. It is the right place to read attested morphosyntax of prose.

## Related

- [[concepts/old-english-case-government]]
- [[concepts/old-english-lemmatisation]]
- [[entities/nerthus-project]]

## Sources

- [YCOE POS manual](https://www-users.york.ac.uk/~lang18/Documentation/pos-manual-oe.htm)
- [[references/miani-2025-oe-poetry-pos]]
- [[references/computational-study-of-old-english-2025]]
