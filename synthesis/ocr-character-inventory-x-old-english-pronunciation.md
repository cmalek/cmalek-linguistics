---
title: >-
    OCR Character Inventory × Old English Pronunciation
category: synthesis
tags: [ocr, old-english, phonology, unicode]
relationships:
  - target: "[[concepts/ocr-character-inventory]]"
    type: derived_from
  - target: "[[concepts/old-english-pronunciation]]"
    type: derived_from
  - target: "[[concepts/old-english-g-palatalization]]"
    type: related_to
sources:
  - "[[concepts/ocr-character-inventory]]"
  - "[[concepts/old-english-pronunciation]]"
  - "[[concepts/ocr-evaluation-metrics]]"
  - "[[references/mufi-character-recommendation]]"
summary: >-
    The marks an Old English textbook adds for pronunciation (macrons, dotted ċ ġ) are the rarest characters an OCR model must emit and the ones a global error rate hides.
provenance:
  extracted: 0.20
  inferred: 0.70
  ambiguous: 0.10
base_confidence: 0.72
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T19:00:00Z
updated: 2026-10-18T19:00:00Z
---

# OCR Character Inventory × Old English Pronunciation

## The Connection

[[concepts/ocr-character-inventory]] says a recognizer only emits characters it was trained to emit. [[concepts/old-english-pronunciation]] says the macrons and the dotted ċ/ġ are modern teaching marks, absent from the manuscripts. Put together: the inventory an OCR model needs for a teaching edition is set by the editor's pedagogy, not by the language. ^[inferred]

## Where They Co-occur

- The inventory page tells you to build the character set from the book and to start from the pronunciation page: þ ð æ ǣ ƿ ȝ, macron vowels, ċ ġ.
- The pronunciation page names the same marks as "part of the copy target" when printed in a PDF.
- [[concepts/ocr-evaluation-metrics]] warns that one overall CER hides a dropped macron.

## Cross-cutting Insight

Each added mark is a decision the editor already made for the reader. A dot on ġ settles [j] versus [ɡ]; a macron settles vowel length ([[concepts/old-english-g-palatalization]] stays unresolvable from plain `g`). These are also the least frequent characters on the page. So the characters that carry the most editorial information are the ones a model sees least often in training and a global CER weights least. A model that drops every ġ can still score well and has erased an analysis. ^[inferred]

Two corollaries follow from the pronunciation page:

- The inventory differs between textbooks. Palatal *c* has no settled narrow IPA, wynn may be respelled *w*, and some editions skip macrons. There is no single "Old English" inventory to download. ^[inferred]
- þ and ð are not sound-conditioned in the manuscripts, and scribes did not reserve þ for [θ]. A post-correction step that "fixes" þ/ð from the voicing rules would invent a distinction the sources lack.

## Tensions and Trade-offs

- Precomposed `ċ` (`U+010B`) survives search and diff better, but the pronunciation page's marks may be printed as base plus a combining dot. Normalizing to NFC hides a composed/decomposed split that the scoring tool also hides.
- Closed inventory (Kraken `new` codec) versus open (`union`): a later page may introduce a mark the first pages never showed, such as an IPA symbol in a phonology chapter.

## Strongest Objection

The pairing may be trivial: any scholarly print with diacritics has this problem, and Old English adds nothing specific beyond a longer list. The claim that marks are both rarest and most informative is an argument from two pages, not a measurement.

> test: on held-out lines from a fine-tuned model, is per-character CER for ċ ġ and macron vowels several times the overall CER?

## Open Questions

- Does oversampling lines with ċ/ġ (as in the IPA study) lift those characters without hurting ordinary Latin letters?
- Which marks are in the textbook the user actually plans to scan? That sets the inventory (see open thread t7).

## Related

- [[concepts/ocr-character-inventory]]
- [[concepts/old-english-pronunciation]]
- [[concepts/old-english-g-palatalization]]
- [[concepts/ocr-evaluation-metrics]]
- [[synthesis/Research: Scholarly PDF to Markdown]]
