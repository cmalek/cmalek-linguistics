---
title: >-
  Cross-genre POS tagging for Old English poetry (2025)
category: references
tags: [old-english, pos-tagging, poetry]
sources:
  - "url:https://aclanthology.org/2025.acl-srw.46.pdf"
source_url: "https://aclanthology.org/2025.acl-srw.46.pdf"
relationships:
  - target: "[[concepts/old-english-lemmatisation]]"
    type: related_to
  - target: "[[entities/ycoe]]"
    type: uses
summary: >-
  ACL 2025: YCOE prose and poetry tagsets differ, and extra prose does not by itself make a poetry POS tagger.
provenance:
  extracted: 0.86
  inferred: 0.10
  ambiguous: 0.04
base_confidence: 0.67
lifecycle: draft
lifecycle_changed: 2026-10-09
tier: supporting
created: 2026-10-09T19:50:00Z
updated: 2026-10-09T19:50:00Z
---

# Cross-genre POS tagging for Old English poetry (2025)

Irene Miani, Sara Stymne, and Gregory Darwin, “Cross-Genre Learning for Old English Poetry POS Tagging,” *Proceedings of the 63rd Annual Meeting of the Association for Computational Linguistics (Volume 4: Student Research Workshop)*, 2025, pp. 708–724. [PDF](https://aclanthology.org/2025.acl-srw.46.pdf).

## Tag inventories

They train on the York–Helsinki Parsed Corpus of Old English Poetry (YCOEP, 2001) and [[entities/ycoe|YCOE]] prose (2003). Poetry has **201** POS tags, prose **289**, and only **173** labels are shared. Differences include spelling errors in the tags, comparative and superlative marked in prose and missing in poetry, `MAN` present only in prose, and proper nouns tagged `NPR` in poetry and `NR` in prose.

Mapping both sets onto Universal Dependencies UPOS cuts the label set to 17 and **drops case, gender, and number**. Their mapping rules: a preposition with a complement becomes `ADP`, a preposition without one becomes `ADV`, and a participle that shows case becomes `ADJ` even though neither corpus tags participles as adjectives. *bēon* and *habban* become `AUX` only under two syntactic tests they define. Contracted negation and particle prefixes (`NEG+`, `RP+`) are stripped back to the core tag.

## Transfer

They state that studies of POS taggers aimed at Old English poetry are lacking, and that the one available tagger is CLTK’s, trained on the ISWOC treebank (Bech and Eide 2014), with accuracy they call uncertain.

The experimental claim: when prose and poetry diverge, adding more prose does not by itself raise poetry accuracy. A small amount of target-genre data beats a model that never saw poetry. A generator or tagger built only on late West Saxon prose will miss poetic diction for this reason, separate from the missing-lemma problem. ^[inferred]

## Related

- [[concepts/old-english-lemmatisation]]
- [[references/ycoe-case-and-pos-annotation]]
- [[references/martin-arista-2026-oe-lemmatisation]]

## Sources

- [ACL Anthology 2025.acl-srw.46](https://aclanthology.org/2025.acl-srw.46.pdf)
