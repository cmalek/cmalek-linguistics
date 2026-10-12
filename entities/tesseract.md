---
title: >-
    Tesseract
category: entities
tags: [ocr, tools]
summary: >-
    Open LSTM OCR engine. Stock English and Latin models miss IPA and historical letters; the unicharset must include them before fine-tuning.
provenance:
  extracted: 0.80
  inferred: 0.16
  ambiguous: 0.04
base_confidence: 0.70
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:20:00Z
relationships:
  - target: "[[concepts/ocr-character-inventory]]"
    type: implements
  - target: "[[references/ocr-for-the-ipa]]"
    type: related_to
sources:
  - "url:https://aclanthology.org/2026.eacl-short.19.pdf"
  - "url:https://tesseractocr.org/train/"
  - "url:http://springmann.net/papers/2018-OCR4Hist-jlcl_2018-1_5.pdf"
---

# Tesseract

[Tesseract](https://github.com/tesseract-ocr/tesseract) is the usual open OCR engine for printed lines. [[entities/docling]] can call it as one OCR plugin. It is a recognizer. Page layout, tables, and markdown are someone else’s job.

## Character coverage

- [[references/ocr-for-the-ipa]]: `eng` and `lat` checkpoints sit near 33–36% CER on IPA until fine-tuned. `lat`’s larger diacritic set barely helps. After synthetic IPA fine-tuning, Latin-based CER falls to about 11.9 on Japhug and 4.4 on the synthetic test. Calamari still wins that paper.
- Training with tesstrain uses one line image plus a `.gt.txt`. The `unicharset` has to contain every glyph you expect, including punctuation. A character missing from that set is never emitted. Fine-tuning must start from a checkpoint whose output layer already has those characters, or you train a new head.
- `isl.traineddata` is modern Icelandic from Wikipedia text. [[references/state-of-icelandic-ocr]] says it has no published Icelandic evaluation and fails on Fraktur. þ/p confusions show up even in newer vision models.
- Fraktur checkpoints (`frk`, `deu_frak`, `script/Fraktur`) exist. The tesstrain wiki and Springmann’s GT4HistOCR paper (JLCL 2018) say the synthetic-only models mishandle long s and ligatures such as ch and tz. GT4HistOCR is real line images from the Deutsches Textarchiv plus early modern Latin, and is the ground truth to prefer for that type.
- hOCR can carry a bold class when the engine detected one. The AMTA 2022 report says the Tesseract they used did not detect bold or italic. Treat style from Tesseract as optional, and take style from the text layer when you have one. See [[concepts/typography-as-linguistic-signal]].

## Related

- [[entities/calamari-ocr]]
- [[entities/kraken]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- [[references/ocr-for-the-ipa]]
- <https://tesseractocr.org/train/>
- <http://springmann.net/papers/2018-OCR4Hist-jlcl_2018-1_5.pdf>
- [[references/state-of-icelandic-ocr]]
