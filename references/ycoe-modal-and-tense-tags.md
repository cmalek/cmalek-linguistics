---
title: >-
  YCOE Modal and Tense Tags
category: references
tags: [old-english, corpus, tense]
sources:
  - "url:https://www-users.york.ac.uk/~lang18/Documentation/pos-manual-oe.htm"
source_url: "https://www-users.york.ac.uk/~lang18/Documentation/pos-manual-oe.htm"
relationships:
  - target: "[[entities/ycoe]]"
    type: documents
  - target: "[[concepts/old-english-future-time]]"
    type: related_to
  - target: "[[references/ycoe-case-and-pos-annotation]]"
    type: related_to
summary: >-
  The YCOE manual tags finite verbs as present or past and lists willan senses that include shall and will. It has no future tag.
provenance:
  extracted: 0.86
  inferred: 0.10
  ambiguous: 0.04
base_confidence: 0.70
lifecycle: draft
lifecycle_changed: 2026-10-12
tier: supporting
created: 2026-10-12T22:05:00Z
updated: 2026-10-12T22:05:00Z
---

# YCOE Modal and Tense Tags

The prose part-of-speech manual for the [[entities/ycoe|York-Toronto-Helsinki Parsed Corpus of Old English]] states how annotators label verbs: [pos-manual-oe.htm](https://www-users.york.ac.uk/~lang18/Documentation/pos-manual-oe.htm). Case rules in the same manual are [[references/ycoe-case-and-pos-annotation]]. This page is only the tense and modal slice.

## Key claims

- Modal tags encode tense and mood of the modal itself: `MDPI` present indicative, `MDPS` present subjunctive, `MDP` present ambiguous between those, `MDPH` present ambiguous between subjunctive and imperative, `MDDI` past indicative, `MDDS` past subjunctive, `MDD` past ambiguous, `MD` infinitive, `MDI` imperative. There is no future label.
- These verbs are tagged modal whether they take an infinitive or stand alone: *cunnan*, *durran* (the manual’s dare verb), *magan*, *mōtan*, *sculan*, *þurfan*, *willan*. *Āgan* is modal only with an infinitive, in the sense ‘have to, ought to’.
- The manual’s gloss for *sculan* is obligation and debt: “to be obliged to, have to, must, ought to, owe.”
- The gloss for *willan* is “be willing to, wish to, desire to, be used to, be about to, shall, will,” and as a main verb “wish, desire.” Future and immediate-future readings are listed inside the lexical gloss, not as a tense feature.
- In the parsed files a modal is a lexical category even when it is the only verb. The manual contrasts that with the Middle English corpus (PPCME2), where an independent modal can be tagged as an ordinary verb.

A search for “future” in this annotation scheme will miss future time. Future time is a present finite verb, or a present modal whose gloss happens to allow *shall* or *will*.

## Limits

The glosses are sense lists for taggers, not a semantic classification of tokens. They do not say how often *willan* means ‘wish’ and how often it means ‘will’.

## Sources

- [YCOE POS manual](https://www-users.york.ac.uk/~lang18/Documentation/pos-manual-oe.htm)
