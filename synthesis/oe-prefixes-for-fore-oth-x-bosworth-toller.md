---
title: >-
    Old English for-, fore-, and oþ- Prefixes × Bosworth-Toller
category: synthesis
tags: [old-english, lexicography, prefixes, tooling]
relationships:
  - target: "[[concepts/oe-prefixes-for-fore-oth]]"
    type: derived_from
  - target: "[[entities/bosworth-toller]]"
    type: derived_from
  - target: "[[concepts/old-english-lemmatisation]]"
    type: related_to
sources:
  - "[[concepts/oe-prefixes-for-fore-oth]]"
  - "[[entities/bosworth-toller]]"
  - "[[concepts/oe-word-formation]]"
  - "[[concepts/old-english-lemmatisation]]"
summary: >-
    The flagged clash over for-/fore- length marks also matters downstream: a generator that takes Bosworth-Toller as its lemma list inherits editorial splits as separate lemmas.
provenance:
  extracted: 0.20
  inferred: 0.65
  ambiguous: 0.15
base_confidence: 0.45
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T19:00:00Z
updated: 2026-10-18T19:00:00Z
---

# Old English for-, fore-, and oþ- Prefixes × Bosworth-Toller

## The Connection

[[concepts/oe-prefixes-for-fore-oth]] contradicts [[entities/bosworth-toller]] (flagged in `hot.md`): Alcorn finds no evidence for a long vowel in any form of FOR and criticizes B–T's four-way division, and the macrons in *fōre-* and *ōþ-* are editorial. That reads as a scholarly dispute. [[entities/bosworth-toller]] also says Tichý uses it as the lemma list for his generator, so the dispute has a tooling consequence. ^[inferred]

## Where They Co-occur

- The prefix page notes that B–T itself says *for-* and *fore-* are frequently confused despite different meanings, then separates *for-/fore-* from *fōr-/fōre-*.
- The prefix page's closing advice: a lemmatiser or dictionary schema should not mint prefix entries from macron differences ([[concepts/old-english-lemmatisation]]).
- [[concepts/oe-word-formation]] (Mitchell) lists *for-* as intensive and does not list *fore-* in its prefix inventory, so the textbook layer and the dictionary layer disagree by omission.

## Cross-cutting Insight

The contradiction is about which layer of B–T to trust. As a citation index (headword, gloss, passages from Maldon, Orosius, Bede) it is not in dispute. As a lexical ontology (how many distinct lemmas exist) its length marks are editorial. Tichý's generator takes it for the second job. Every editorial split becomes a separate lemma, and each lemma gets generated paradigms and lookup hits. Tichý's average token already returns about two lemmas ([[concepts/old-english-lemmatisation]]); editorial duplicates could add to that. ^[inferred]

So the practical rule from the prefix page, "use *fore-* in normalized text, record overlapping senses under *oþ-*", belongs at lexicon-build time, not at lookup time. A normalized headword with sense notes is cheaper than a post-hoc merge of paradigms. ^[inferred]

## Tensions and Trade-offs

- Merging variants loses the dictionary's own distinctions; keeping them inflates the lemma list. The DOE is corpus-built and incomplete, so it cannot yet replace B–T as the lemma source.
- Alcorn's view is the prosodic variant account; B–T's etymological grouping may still be right for individual words.

## Strongest Objection

The prefix page rests on a chat-style note whose citations were "not independently checked", hence its base confidence of 0.45, the lowest of any page in this vault. The synthesis inherits that. Duplicate lemmas from macron splits may also be a handful of entries with no measurable effect on lookup.

> test: how many B–T headwords in *fōr-/fōre-/óþ-* have a counterpart under the unmarked spelling, and does the DOE merge them under one headword?

## Open Questions

- Which *for-/fore-* compounds are genuinely ambiguous in the manuscripts (carried over from the prefix page)?
- Does the Nerthus database store a prefix split, or does it follow B–T's marks?

## Related

- [[concepts/oe-prefixes-for-fore-oth]]
- [[entities/bosworth-toller]]
- [[concepts/oe-word-formation]]
- [[concepts/old-english-lemmatisation]]
- [[synthesis/Research: Old English Morphology Generation]]
