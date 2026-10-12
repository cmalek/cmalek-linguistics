---
title: >-
    Reading or Guessing? VLM OCR on Greek and Arabic Editions
category: references
tags: [ocr, greek, arabic, evaluation]
sources:
  - "url:https://arxiv.org/html/2605.27750v2"
source_url: "https://arxiv.org/html/2605.27750v2"
summary: >-
    Inria 2026: on Greek and Arabic book scans, in-domain Kraken beats VLMs, and VLMs repair implausible letters toward fluent text.
provenance:
  extracted: 0.90
  inferred: 0.08
  ambiguous: 0.02
base_confidence: 0.67
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:20:00Z
relationships:
  - target: "[[concepts/diplomatic-ocr-target]]"
    type: related_to
  - target: "[[entities/kraken]]"
    type: uses
  - target: "[[entities/tesseract]]"
    type: uses
  - target: "[[references/olmocr]]"
    type: related_to
---

# Reading or Guessing? VLM OCR on Greek and Arabic Editions

Antonia Karamolegkou, Nicolas Angleraud, Benoît Sagot, and Thibault Clérice (Inria). [arXiv:2605.27750](https://arxiv.org/html/2605.27750v2).

Compares five open-weight vision-language OCR models with Tesseract and in-domain Kraken on real printed editions: 90 Greek pages (1,966 lines, 16th–20th century) and 140 Arabic pages (3,197 line crops, 19th–20th century). Greek pages include polytonic text, mixed scripts, marginal apparatus, and alphabetic numerals.

## Key claims

- Median CER on Greek: Kraken-CLLG 4.1, LightOnOCR-1B 4.1, Qwen3-VL-8B 5.1, olmOCR-2-7B 6.4, DeepSeek-OCR 6.7, Tesseract-grc 7.5, Qwen3-VL-2B 8.0. On Arabic: Kraken-OpenITI 3.1, olmOCR-2-7B 10.5, Qwen3-VL-8B 11.3, LightOnOCR-1B 15.4, Qwen3-VL-2B 17.6, DeepSeek-OCR 20.8, Tesseract-ara 24.6. The Kraken gap over Tesseract is training data: Kraken is in-domain; Tesseract is mostly synthetic or modern print.
- Only the vision-language models produce repetition collapse, markup emission, and off-script characters (Latin letters inside Arabic lines). Kraken and Tesseract do not. Their output length and alphabet are constrained by the recognition head.
- Accents and diacritics account for 37–57% of vision-language model errors on Greek.
- When the image is altered so the printed letters are linguistically implausible, every vision-language model moves further from the displayed text than either traditional recognizer. Character perturbation raises median CER by 12.61 to 42.45 points (Greek) and 10.55 to 26.24 (Arabic), against 2.53 to 6.05 for Kraken and Tesseract.
- Word-order shuffles, which leave each word image intact, move CER by less than about 2 points. The models are reading the word images. They “repair” unusual character sequences inside those images.
- Inference tricks do not transfer. Script-constrained decoding badly hurts Greek. Text-only language-model correction helps some Greek systems and degrades nearly all Arabic systems.
- Greek and Arabic are scored differently (page vs line, different normalization), so the paper compares rankings inside each language.

## Limitations

The traditional winner is a model trained on the same kind of book. A generic Kraken Latin model is not what they measured. The study is recognition of existing lines, not a PDF-to-Markdown layout pipeline.

## Related

- [[concepts/diplomatic-ocr-target]] — fluency is the wrong success test
- [[entities/kraken]] — collection-specific recognizer
- [[entities/regreek]] — a non-OCR path for born-digital polytonic Greek
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- <https://arxiv.org/html/2605.27750v2>
