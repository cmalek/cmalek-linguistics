---
title: >-
  YCOE case and POS annotation
category: references
tags: [old-english, corpus, syntax]
sources:
  - "url:https://www-users.york.ac.uk/~lang18/Documentation/pos-manual-oe.htm"
source_url: "https://www-users.york.ac.uk/~lang18/Documentation/pos-manual-oe.htm"
relationships:
  - target: "[[entities/ycoe]]"
    type: related_to
  - target: "[[concepts/old-english-case-government]]"
    type: related_to
  - target: "[[concepts/old-english-lemmatisation]]"
    type: uses
summary: >-
  YCOE marks case when the form shows it, and refuses to fill ambiguous case from the governing verb or preposition.
provenance:
  extracted: 0.90
  inferred: 0.08
  ambiguous: 0.02
base_confidence: 0.62
lifecycle: draft
lifecycle_changed: 2026-10-09
tier: supporting
created: 2026-10-09T19:50:00Z
updated: 2026-10-09T19:50:00Z
---

# YCOE case and POS annotation

[YCOE POS annotation manual](https://www-users.york.ac.uk/~lang18/Documentation/pos-manual-oe.htm), York, for the [[entities/ycoe|York-Toronto-Helsinki Parsed Corpus of Old English Prose]]. A mirror is hosted with the Penn historical corpora. The tagset is the Penn historical style: a category plus inflection, for example `N^D`, `VBDI`, `PRO^A`. [[references/miani-2025-oe-poetry-pos|Miani, Stymne, and Darwin (2025)]] count 289 prose tags and 201 poetry tags, with 173 shared.

## Case policy

Case is marked when the form distinguishes it. Nominative is marked on subjects of tensed verbs. Accusative, genitive, and dative are marked when the ending is unambiguous. The manual’s rule for governors is the one that matters for [[concepts/old-english-case-government]]:

Ambiguous complements of verbs and prepositions are **not** labelled from the case the governor usually takes. An accusative/dative complement of a dative-taking verb stays unmarked. The exception is dative/genitive ambiguity: if the verb or preposition is not on the list of genitive-takers, the complement is labelled dative. The manual says this was an efficiency choice, because a reliable case requirement was not at hand for every verb in the corpus. The same rules apply to prepositions.

For prepositions, accusative/dative ambiguity is never resolved. Few prepositions take the genitive. With *tō*, genitive is rare, so genitive/dative is resolved toward dative and only unambiguous genitives are labelled genitive. With *wiþ*, the cases are treated as evenly distributed, so only unambiguous forms are labelled.

First- and second-person singular and plural pronouns in the prose are accusative/dative ambiguous and are generally not case-labelled except in copular constructions. Possessives *his*, *hire*, *heora* are not case-tagged. *mīn*, *þīn*, *uncer*, *ūre*, *incer*, *ēower* decline like adjectives and are case-marked.

## What a generator cannot read off YCOE

The corpus is the largest morphosyntactically annotated Old English prose sample, and it was built so that it would **not** invent government. A lexicon of “this verb governs the dative” has to come from somewhere else: Mitchell’s *Old English Syntax* (1985), which the manual cites for verbs that can take the genitive, or a valency database such as [[references/paveda-old-english-valency|PaVeDa]].

## Related

- [[concepts/old-english-case-government]]
- [[concepts/old-english-lemmatisation]]
- [[references/paveda-old-english-valency]]

## Sources

- [YCOE POS annotation manual](https://www-users.york.ac.uk/~lang18/Documentation/pos-manual-oe.htm)
