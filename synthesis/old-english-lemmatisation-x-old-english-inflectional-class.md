---
title: >-
    Old English Lemmatisation × Old English Inflectional Class
category: synthesis
tags: [old-english, lemmatisation, morphology, nlp]
relationships:
  - target: "[[concepts/old-english-lemmatisation]]"
    type: derived_from
  - target: "[[concepts/old-english-inflectional-class]]"
    type: derived_from
  - target: "[[concepts/old-english-form-generation]]"
    type: related_to
sources:
  - "[[concepts/old-english-lemmatisation]]"
  - "[[concepts/old-english-inflectional-class]]"
  - "[[concepts/old-english-form-generation]]"
  - "[[concepts/oe-word-formation]]"
summary: >-
    Neural lemmatiser errors cluster on strong-verb ablaut, the one field its output never states: inflectional class. Class is the missing variable, and compounds show it most.
provenance:
  extracted: 0.20
  inferred: 0.70
  ambiguous: 0.10
base_confidence: 0.73
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T19:00:00Z
updated: 2026-10-18T19:00:00Z
---

# Old English Lemmatisation × Old English Inflectional Class

## The Connection

[[concepts/old-english-lemmatisation]] asks for a headword per token. [[concepts/old-english-inflectional-class]] says generation needs the paradigm, and UPOS tags do not carry it. Both pages already say that the 2026 Transformer "never emits stem class or case". They do not say that this is also where it fails. ^[inferred]

## Where They Co-occur

- Lemmatisation page: Martín Arista (2026) reaches 67.58 percent lemma accuracy; errors concentrate on strong-verb ablaut, spelling, and *ge-*.
- Class page: strong-verb subclasses follow Krygier; Tichý explodes verbs to 132 classes; the model card assigns about a quarter of errors to ablaut and verb UPOS accuracy is about 55 percent.
- Both mention [[concepts/old-english-form-generation]] as the inverse task.

## Cross-cutting Insight

Ablaut series are the strong classes. A token like *sungon* is recoverable as *singan* only if the model knows the class pattern that links the vowels. The model must infer a class it is never asked to output and has no labels for: YCOE tags encode case, number, tense, and mood but "do not store this noun is an i-stem". Nerthus has the class labels and YCOE has the context, and they are different resources. The cheapest hypothesis for the 68 percent figure is a missing variable, not a weak model. ^[inferred]

Compounds show the same gap from the other side. Poetry lemmatisation invented 72 lemmas, mostly compounds. The class page says a compound inherits its class from its second element, and *ge-beran* takes the class of *beran*. So a lemmatiser that segments a compound correctly could assign the class without a dictionary entry, and one that does not cannot be generated back into paradigm cells. ^[inferred]

## Tensions and Trade-offs

- Recall versus exact match: Tichý's 95 percent counts a hit anywhere in the list; the Transformer must emit one string. Adding class output makes the second task harder before it helps.
- Label granularity: 7 strong classes, Krygier's subclasses, or 132 machine classes. Human agreement is itself around 90–95 percent, so finer labels may exceed annotator consistency.

## Strongest Objection

The ablaut errors may come from spelling variation and sparse strong-verb types, with class unlabeled as a coincidence. Gold inconsistency is already 11.3 percent of types, so any gain from adding class could be smaller than the noise.

> test: does adding Nerthus class labels as an auxiliary target raise strong-verb lemma accuracy on YCOE above 67.58 percent, and by more than the gold inconsistency rate?

## Open Questions

- Can Tichý-style candidate lists (each lemma with its class pattern) be used to re-rank neural output?
- How many YCOE lemmas have no Nerthus match, and therefore no class to copy?

## Related

- [[concepts/old-english-lemmatisation]]
- [[concepts/old-english-inflectional-class]]
- [[concepts/old-english-form-generation]]
- [[concepts/oe-word-formation]]
- [[synthesis/Research: Old English Morphology Generation]]
