---
title: >-
    Kraken
category: entities
tags: [ocr, htr, tools]
summary: >-
    Open OCR/HTR engine for historical print and handwriting. Accuracy depends on a model trained for that script and type.
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
  - target: "[[concepts/diplomatic-ocr-target]]"
    type: related_to
sources:
  - "url:https://kraken.re/7.0/introduction_to_atr.html"
  - "url:https://escriptorium.eu/transcribe/"
  - "url:https://arxiv.org/html/2605.27750v2"
---

# Kraken

[Kraken](https://kraken.re/7.0/introduction_to_atr.html) (Benjamin Kiessling) finds lines, then recognizes each line image as a character sequence. [eScriptorium](https://escriptorium.eu/transcribe/) is the web application that trains and runs it. Models on Zenodo cover medieval Latin and other scripts. A model is a script-and-type skill: modern English weights do not read medieval Latin.

## What it is for

- Print with rare type, incunabula, and handwriting, once you can correct a sample and fine-tune.
- Output is text per line, with coordinates in ALTO or PAGE. That is the input to a TEI or HTML conversion, not a finished markdown file. See [[concepts/scholarly-markdown-limits]].
- The character inventory is the codec of the recognition model. eScriptorium virtual keyboards are how you type thorn, combining marks, and abbreviations into ground truth. See [[concepts/ocr-character-inventory]].
- [[references/reading-or-guessing-vlm-ocr]] finds in-domain Kraken (CLLG for Greek, OpenITI for Arabic) at 4.1% and 3.1% median CER, ahead of general vision-language OCR, and free of repetition and off-script hallucinations.
- [[entities/regreek]] points to the Ciaconna Kraken model for scanned polytonic Greek. Born-digital Greek with a legacy font is a CMap repair, not a Kraken job.
- Transkribus is the other common HTR desk. Its EVMsaurus minimus model (January 2026, PyLaia) reads English vernacular minuscule, including thorn, eth, wynn, and Tironian marks, at 4.96% CER on its validation set. That is a manuscript model. It does not replace a print recognizer for a modern textbook.

Fine-tuning loads a checkpoint and keeps training. Two codec modes matter when the book has letters the base model lacks: `union` adds them, `new` replaces the alphabet with whatever is in the new ground truth. See [[concepts/ocr-character-inventory]]. Mannheim’s guide: a Latin model misses a new symbol until that symbol is in the corrected lines, and 2–3 corrected pages are enough to start if the base model already roughly reads the type. [[concepts/ocr-human-correction]].

Binarization is deprecated for the baseline segmenter and can hurt faint or uneven pages. Recognize from grayscale or color unless the checkpoint was trained on binary images. The legacy box segmenter still requires binary input. [[concepts/ocr-page-images]].

The default baseline model emits one line type and one generic region. A grammar page needs region labels (body, table, note, apparatus) before reading order is trustworthy. [[concepts/ocr-pipeline]].

## Related

- [[skills/linguistic-pdf-to-markdown]]
- [[entities/tesseract]]
- [[entities/escriptorium]]
- [[entities/calamari-ocr]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- <https://kraken.re/7.0/introduction_to_atr.html>
- <https://escriptorium.eu/transcribe/>
- <https://www.transkribus.org/models/evmsaurus-minimus>
- [[references/reading-or-guessing-vlm-ocr]]
