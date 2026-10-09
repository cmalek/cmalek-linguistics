---
title: >-
    Kurdi Morphology Sphere
category: concepts
tags: [nlp, linguistics, morphology]
relationships:
  - target: "[[concepts/nlp-corpus]]"
    type: related_to
  - target: "[[concepts/old-english-grammar]]"
    type: related_to
  - target: "[[concepts/kurdi-syntax]]"
    type: related_to
sources:
  - "url:https://learning.oreilly.com/library/view/natural-language-processing/9781848218482/chapter3.xhtml"
summary: "Kurdi: words from morphemes; isolating vs fusional vs agglutinative types; English stem-plus-affix morphology."
provenance:
  extracted: 0.92
  inferred: 0.06
  ambiguous: 0.02
base_confidence: 0.57
lifecycle: draft
lifecycle_changed: "2026-09-25"
tier: supporting
created: 2026-09-25T16:40:00Z
updated: 2026-09-25T16:40:00Z
snapshots:
  - "[[_raw/_archived/Kurdi 3 Morphology Sphere]]"
---

# Kurdi Morphology Sphere

From Mohamed Zakaria Kurdi (2016), *Natural Language Processing and Computational Linguistics*, ch. 3. Morphology studies how words are built from **morphemes** (smallest meaningful units). Simple words (*book*) vs complex (*books*, *finished*).

## Key Ideas

- **Lexical morphemes** (open class, neologisms possible) vs **grammatical morphemes** (closed: prepositions, articles, pronouns).
- Independence of morphology is not unanimous: Distributed Morphology (Halle) lets syntax do word-building too; phonology and morphology interact (e.g. plural allomorphy); meaning of an utterance is a function of morpheme meanings.
- **Typology**
  - *Isolating / analytic* (Vietnamese, Chinese): morpheme-to-word ratio near 1:1; order carries what inflection would.
  - *Fusional* (Arabic *k-t-b* → *kataba*, *kitab*, *maktaba*): internal modification of a stem, not just edge affixes.
  - *Agglutinative* (Turkish): separable suffixes stacked, sometimes a whole clause (*sütsüz* “without milk”).
  - Mixed systems exist (Japanese).
- **English:** stem plus optional affixes; Latin/Greek/French/etc. loans enrich the inventory. The stem cannot be stripped (*book* stays if *-s* is removed).

[[concepts/old-english-grammar]] is a fusional/synthetic Germanic system in Kurdi’s terms: stem + rich inflection, not isolating. ^[inferred]

## Open Questions

- Remaining subsections (derivation vs inflection, NLP stemming/lemmatization) not yet distilled.

## Sources

- Kurdi (2016), ch. 3, via O'Reilly
