---
title: >-
    Kurdi Syntax Sphere
category: concepts
tags: [nlp, linguistics, syntax]
relationships:
  - target: "[[concepts/kurdi-morphology]]"
    type: related_to
  - target: "[[concepts/nlp-corpus]]"
    type: related_to
  - target: "[[concepts/old-english-grammar]]"
    type: related_to
sources:
  - "url:https://learning.oreilly.com/library/view/natural-language-processing/9781848218482/chapter4.xhtml"
summary: "Kurdi: syntax as sentence structure and grammaticality (not normative style); constituents, Chomsky vs Tesnière dependency."
provenance:
  extracted: 0.90
  inferred: 0.08
  ambiguous: 0.02
base_confidence: 0.57
lifecycle: draft
lifecycle_changed: "2026-09-25"
tier: supporting
created: 2026-09-25T16:40:00Z
updated: 2026-09-25T16:40:00Z
snapshots:
  - "[[_raw/_archived/Kurdi 4 Syntax Sphere]]"
---

# Kurdi Syntax Sphere

From Kurdi (2016), ch. 4. Syntax studies the sentence as an independent unit: word order, dependency, agreement, case. Goal: formal regularities of combination. It sits next to phonology/prosody (dislocation and clefting ride intonation), morphology (word-internal vs word-external; some theories collapse this to morphosyntax), and semantics (form vs meaning; both needed for ambiguity and anomaly).

## Key Ideas

- In NLP, **grammar is descriptive**: what a community actually says at a time, not schoolroom “correctness.” Chomsky: a grammar is a device that sorts strings into well-formed vs ill-formed (competence).
- Grammaticality ≠ frequency (a rare but well-formed adjective can beat a likely but ill-typed noun). Grammaticality ≠ interpretability (*Me Tarzan, You Jane* is agrammatical and still understood).
- Parsing decomposes sentences into constituents and dependencies (Hockett boxes; trees). Constituents may be words or sequences with a role.
- Some linguists deny units larger than the word: **dependency grammar** (Tesnière; Mel’čuk and others) — still a minority current in modern syntax per Kurdi.
- Word-class / POS tagging is a practical NLP presupposition even when “word” is theoretically messy.

For OE, [[concepts/old-english-grammar]] and the translation algorithm on [[skills/translating-ancient-texts]] are the language-specific counterpart: find clauses, finite verb, then subject. ^[inferred]

## Open Questions

- Phrase-structure vs dependency implementations and the rest of Kurdi’s chapter (1970+ lines) not yet distilled.

## Sources

- Kurdi (2016), ch. 4, via O'Reilly
