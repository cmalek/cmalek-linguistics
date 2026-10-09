---
title: >-
    NLP Corpora
category: concepts
tags: [nlp, linguistics, corpus]
relationships:
  - target: "[[concepts/historical-linguistics-sound-terms]]"
    type: related_to
  - target: "[[skills/translating-ancient-texts]]"
    type: related_to
  - target: "[[concepts/kurdi-morphology]]"
    type: related_to
  - target: "[[concepts/kurdi-syntax]]"
    type: related_to
  - target: "[[concepts/kurdi-lexical-semantics]]"
    type: related_to
sources:
  - "url:https://learning.oreilly.com/library/view/natural-language-processing/9781848218482/chapter1.xhtml"
  - "url:https://learning.oreilly.com/library/view/natural-language-processing/9781848218482/bibliography.xhtml"
  - "url:https://learning.oreilly.com/library/view/natural-language-processing/9781848219212/bibliography.xhtml"
summary: "Kurdi's definition of a linguistic corpus (representativeness, finite size, digital form) and the main taxonomy used in NLP."
provenance:
  extracted: 0.90
  inferred: 0.08
  ambiguous: 0.02
base_confidence: 0.78
lifecycle: draft
lifecycle_changed: "2026-09-25"
tier: supporting
created: 2026-09-25T16:30:00Z
updated: 2026-09-25T16:55:00Z
snapshots:
  - "[[_raw/_archived/Kurdi 1 Linguistic Resources for NLP]]"
  - "[[_raw/_archived/Kurdi 2017 Bibliography]]"
  - "[[_raw/_archived/Kurdi Bibliography]]"
---

# NLP Corpora

From Mohamed Zakaria Kurdi (2016), *Natural Language Processing and Computational Linguistics*, ch. 1. A corpus is a collection of linguistic data chosen for description or application — not “the language itself.”

## Key Ideas

**Definitions Kurdi quotes:** Crystal: data (written or transcribed speech) as starting point or hypothesis check. Sinclair: naturally occurring text chosen to characterize a state or variety. Dubois: the corpus reflects the artificial situation of recording, not a constituent of the language.

**Design properties commonly required:** representativeness, finite predetermined size, electronic format. Chomsky's objection (rare but grammatical phenomena may never appear; language is infinite) is answered practically: size follows the task; a 10,000-word grammatical sentence is irrelevant to hotel-domain MT. Open/continually updated collections (Sinclair/Birmingham) trade the “finite” criterion for diachronic representativeness (neologisms).

**Digital issues:** portability across software generations; XML / EAGLES CES / XCES as survival formats.

**Taxonomy (selected):**

- Written vs spoken (and spoken subtypes: dictation, commands, human–machine dialogue, machine-mediated human dialogue, multimodal).
- Historical vs contemporary (ancient spoken language is essentially unrecoverable).
- Monolingual vs parallel vs multilingual-but-not-parallel (CALLFRIEND/CALLHOME). Parallel corpora need alignment (length, lexical, hybrid; GIZA++).
- Thematic layout: balanced, pyramidal, or opportunistic. Topic labels are messy; no agreed text typology (Dewdney).
- Speaker age: ATIS (adults), CHILDES (acquisition), NICE (adolescents).

For this vault, OE text collections are historical written corpora in Kurdi's sense; using them for NLP still inherits representativeness limits (literary/religious bias). ^[inferred]

**Bibliography as a map (not a dump):** the 2016 volume’s list is speech/morphology/syntax-heavy — Abney chunking, Bird/Klein/Loper *NLP with Python*, Beesley finite-state morphology, Chomsky as a foil, ALPAC (1966) on MT. The 2017 list is semantics/discourse/applications-heavy — Austin *How to Do Things with Words*, Adam on text types, Abeillé treebanks, FASTUS IE. Follow those names from [[concepts/kurdi-morphology]] through [[concepts/kurdi-nlp-applications]] rather than treating the bibliographies as pages.

## Open Questions

- Alignment tools named in ch. 1 (GIZA++) versus later neural aligners.

## Sources

- Kurdi (2016), ch. 1, via O'Reilly
- Kurdi (2016) and (2017) bibliographies (selected pointers only)
