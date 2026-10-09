---
title: >-
    Kurdi Combinatorial Semantics
category: concepts
tags: [nlp, linguistics, semantics]
relationships:
  - target: "[[concepts/kurdi-lexical-semantics]]"
    type: related_to
  - target: "[[concepts/kurdi-syntax]]"
    type: related_to
  - target: "[[concepts/kurdi-discourse]]"
    type: related_to
sources:
  - "url:https://learning.oreilly.com/library/view/natural-language-processing/9781848219212/ch02.xhtml"
summary: "Kurdi 2017: Katz–Fodor interpretive semantics — dictionary features plus projection rules over syntactic structure; grammaticality is not world-knowledge."
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
  - "[[_raw/_archived/Kurdi 2017 2 The Sphere of Semantics]]"
---

# Kurdi Combinatorial Semantics

From Kurdi (2017), ch. 2. Lexicon plus syntax is not enough: high-level semantic constraints pick roles (agent vs undergoer: *John writes* vs *John dies* vs *it is raining*).

## Key Ideas

- **Interpretive semantics** (Fodor & Katz 1964): enrich syntactic trees. Semantics lists *possible* readings independent of world knowledge; pragmatics is the rest. Goals: count/content of readings, detect anomaly, detect paraphrase.
- Two pieces given a prior grammatical analysis: a **dictionary** (POS + markers ±human, ±concrete, ±animate, plus redundancy e.g. +human → +animate) and **projection rules** for combining senses in constituents.
- Ambiguity multiplies (*drive* × *car* × *colorful* = 24). Projection **selective restrictions** kill combinations (*drive* = “motivate” needs an animate object, not *car*).
- **Katz–Postal:** transformations do not change meaning; interpret at deep structure (fits Chomsky 1957/65: generate skeletons, insert lexicon, transform to surface). Later Chomsky: surface properties such as stress also matter (*Mary bought her laptop at the store’*).

See [[concepts/kurdi-syntax]] for grammaticality vs interpretability.

## Open Questions

- Later generative-semantics debate and NLP implementations not yet distilled.

## Sources

- Kurdi (2017), ch. 2, via O'Reilly
