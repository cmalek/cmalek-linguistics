---
title: >-
    Seven Million Pages Nobody Can Read
category: references
tags: [ocr, icelandic, old-norse, evaluation]
sources:
  - "url:https://sigurdurhaukur.com/articles/ocr-lit-review"
source_url: "https://sigurdurhaukur.com/articles/ocr-lit-review"
summary: >-
    2026 survey of Icelandic OCR: þ/ð/æ and accent errors are systematic, Fraktur archives are unusable, and print OCR is a different job from handwriting.
provenance:
  extracted: 0.80
  inferred: 0.14
  ambiguous: 0.06
base_confidence: 0.45
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:20:00Z
relationships:
  - target: "[[concepts/ocr-character-inventory]]"
    type: related_to
  - target: "[[concepts/diplomatic-ocr-target]]"
    type: related_to
  - target: "[[entities/tesseract]]"
    type: related_to
---

# Seven Million Pages Nobody Can Read

Sigurdur Haukur Birgisson, 2 June 2026. [sigurdurhaukur.com/articles/ocr-lit-review](https://sigurdurhaukur.com/articles/ocr-lit-review). A literature survey of Icelandic newspaper and book OCR (Tímarit.is, about 7 million pages; Bækur.is). It is a secondary source. The numbers below are the survey’s citations of Jasonarson et al., Steingrímsson et al. (MC-19), Kargaran et al., and the CEMI project.

## Key claims

- Generic engines misread Þ/þ, Ð/ð, Æ/æ, and á é í ó ú ý. On 375k tokens of corrected 19th-century text, Jasonarson et al. count p confused with þ 2,779 times, i with í 1,141 times, and rn with m 166 times. Kargaran et al. report the same þ/p and ð/d confusions in vision-language models trained mostly on English.
- Icelandic inflection makes many of those errors real words. A spellchecker that only flags non-words misses them.
- CEMI (1540–1850 manuscripts and print) keeps OCR correction and spelling normalization as separate stages. A modern-Icelandic model asked to do both will modernize the page while “fixing” it.
- Fraktur periodicals from 1800–1920 on Tímarit.is were effectively unusable in Steingrímsson et al.’s check. Jasonarson et al. identify that OCR as ABBYY FineReader. Tesseract `isl.traineddata` is synthetic text from Icelandic Wikipedia in modern Latin fonts. The survey says it has no published evaluation on an Icelandic test set, and MC-19 found it unusable on Fraktur.
- Print OCR and handwriting recognition do not transfer. Most of the cited work is print. There is still no public image–text benchmark: post-correction deposits store the corrected string and drop the link to the line image.
- The survey’s own conclusion: on clean modern print, þ/ð errors are learnable if the training text actually contains them.

## Limitations

Blog confidence is lower than the papers it cites. The þ/p counts are 19th-century print, not a modern Old Norse textbook set in Junicode. The direction of the error (“p confused with þ”) is the survey’s wording of Jasonarson’s table. ^[ambiguous]

## Related

- [[concepts/ocr-character-inventory]]
- [[concepts/diplomatic-ocr-target]]
- [[entities/tesseract]]
- [[concepts/old-norse-grammar]] — the letters this inventory has to keep
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- <https://sigurdurhaukur.com/articles/ocr-lit-review>
