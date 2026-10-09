---
title: >-
    Kurdi NLP Applications
category: concepts
tags: [nlp, linguistics, applications]
relationships:
  - target: "[[concepts/kurdi-discourse]]"
    type: related_to
  - target: "[[concepts/nlp-corpus]]"
    type: related_to
  - target: "[[concepts/kurdi-lexical-semantics]]"
    type: related_to
sources:
  - "url:https://learning.oreilly.com/library/view/natural-language-processing/9781848219212/ch04.xhtml"
summary: "Kurdi 2017 ch. 4: combine speech–morphology–syntax–semantics–discourse into human-usable NLP software; lifecycle, architecture, evaluation."
provenance:
  extracted: 0.90
  inferred: 0.08
  ambiguous: 0.02
base_confidence: 0.57
lifecycle: draft
lifecycle_changed: "2026-09-25"
tier: supporting
created: 2026-09-25T16:50:00Z
updated: 2026-09-25T16:50:00Z
snapshots:
  - "[[_raw/_archived/Kurdi 2017 4 The Sphere of Applications]]"
---

# Kurdi NLP Applications

From Kurdi (2017), *NLP and Computational Linguistics 2*, ch. 4. Earlier chapters treat levels separately ([[concepts/kurdi-morphology]], [[concepts/kurdi-syntax]], [[concepts/kurdi-lexical-semantics]], [[concepts/kurdi-combinatorial-semantics]], [[concepts/kurdi-discourse]]). This chapter **combines** those levels with other knowledge to build software people actually use.

## Key Ideas

- Extra attention to what is distinctive about NLP products: **development cycle**, **architecture**, and **evaluation**.
- Lifecycle (need → specifications → design/docs/pseudocode → modular coding overlapping tests → maintenance). NLP often inserts **data collection** between design and coding (methods in the 2016 volume’s resources chapters / [[concepts/nlp-corpus]]).
- Need can come from research, everyday public use, or a business opportunity. Tests are modular then integration. Maintenance checks that prerequisites still hold.

Later sections of the chapter (specific application families and metrics) are not yet distilled.

## Open Questions

- Which application types and evaluation measures Kurdi treats after §4.1.

## Sources

- Kurdi (2017), ch. 4, via O'Reilly
