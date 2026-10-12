---
title: >-
    OCR Pipeline
category: concepts
tags: [ocr, workflow, layout]
summary: >-
    Four stages, tuned separately: page image, regions and lines, character recognition, then a diplomatic check. Fine-tune the recognizer on corrected lines.
provenance:
  extracted: 0.70
  inferred: 0.24
  ambiguous: 0.06
base_confidence: 0.75
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:45:00Z
updated: 2026-10-09T18:45:00Z
relationships:
  - target: "[[concepts/ocr-page-images]]"
    type: uses
  - target: "[[concepts/ocr-human-correction]]"
    type: uses
  - target: "[[concepts/ocr-evaluation-metrics]]"
    type: uses
  - target: "[[entities/kraken]]"
    type: implements
sources:
  - "url:https://kraken.re/6.0.0/tutorials/training.html"
  - "url:https://arxiv.org/pdf/2106.07881"
  - "url:https://ub-mannheim.github.io/eScriptorium_Dokumentation/Training-with-eScriptorium-EN.html"
---

# OCR Pipeline

A page image goes through layout, then line recognition, then reading order. Those are different models. A bad line split cannot be fixed by a better character model. [[entities/kraken]] trains segmentation, reading order, and recognition separately. [[entities/escriptorium]] runs that loop in a browser.

## Stages

1. **Image.** One page, one file, recipe frozen. [[concepts/ocr-page-images]].
2. **Regions and baselines.** A baseline model finds text lines even when they curve. The default Kraken model emits one line type and one generic text region, which is enough for a simple page and wrong for a grammar: body, paradigm table, footnote, apparatus, and marginal gloss need different region labels (SegmOnto is the usual controlled vocabulary). Correct the lines before you transcribe. Training on a bad polygon teaches the next model the same bad polygon.
3. **Recognition.** Each line image becomes a character string. The string can only contain the model’s codec. [[concepts/ocr-character-inventory]]. Start from a model whose type is close (Latin print, or a medieval Latin model such as CATMuS print), then fine-tune. Training from scratch wants a very large set; Mannheim’s eScriptorium guide says hundreds of thousands of lines and recommends the command line for that scale.
4. **Order and export.** Reading order is its own model, tied to the region types it was trained on. Export ALTO or PAGE with coordinates. Markdown comes later, from HTML or TEI. [[concepts/scholarly-markdown-limits]].

## What to tune, and in which order

Measure each stage on a held-out sample before you tune the next. [[concepts/ocr-evaluation-metrics]].

- If lines are split, merged, or miss a superscript, fix segmentation. Character error rate on a broken line is not a recognizer score.
- If lines are right and þ, macrons, or long s are wrong, fine-tune recognition. See [[concepts/ocr-human-correction]].
- If the characters are right and the paragraph order is wrong, train or correct reading order. Page-level word error mixes this up with recognition error. Vidal and colleagues separate bag-of-words error from reading-order distance for that reason.
- Whitespace merges and splits were the largest error class in [[references/mixed-model-historical-ocr]]. A lexicon pass can target those after the diplomatic string exists. It is not a substitute for the character model.

Vision-language page models skip this split and emit a whole page at once. They also invent and normalize. [[references/reading-or-guessing-vlm-ocr]]. For a diplomatic target, a line recognizer with a closed codec is the controllable piece. A page model can still propose layout. It should not be the only source of the letters. ^[inferred]

## Related

- [[skills/linguistic-pdf-to-markdown]]
- [[entities/calamari-ocr]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- [Kraken training tutorial](https://kraken.re/6.0.0/tutorials/training.html)
- [[references/mixed-model-historical-ocr]]
- [Mannheim eScriptorium training guide](https://ub-mannheim.github.io/eScriptorium_Dokumentation/Training-with-eScriptorium-EN.html)
- [[references/ocr-of-historical-printings]]
