---
title: >-
    Mixed Model OCR for Historical Latin Script
category: references
tags: [ocr, latin, evaluation, training]
sources:
  - "url:https://arxiv.org/pdf/2106.07881"
source_url: "https://arxiv.org/pdf/2106.07881"
summary: >-
    Reul et al. 2021: a polyfont Calamari model near 2% CER on unseen historical books, and finetuning that beats training from scratch.
provenance:
  extracted: 0.88
  inferred: 0.10
  ambiguous: 0.02
base_confidence: 0.67
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:45:00Z
updated: 2026-10-09T18:45:00Z
relationships:
  - target: "[[entities/calamari-ocr]]"
    type: uses
  - target: "[[concepts/ocr-evaluation-metrics]]"
    type: related_to
---

# Mixed Model OCR for Historical Latin Script

Christian Reul, Christoph Wick, Maximilian Nöth, Andreas Büttner, Maximilian Wehner, and Uwe Springmann. HIP 2021. [arXiv:2106.07881](https://arxiv.org/pdf/2106.07881).

## Key claims

- Goal: one Latin-script model, 15th–19th century, Fraktur and Antiqua, several languages, that is usable out of the box and cheap to finetune.
- Training pool is on the order of 21,000 pages (GT4HistOCR, French Antiqua, OCR-D, Fraktur collections). Evaluation is 29 unseen books, 1506–1849, four or five pages each, segmented in OCR4all and transcribed after line correction.
- Best mixed model (LSH-4) is about 1.7–1.8% CER on that set and beats the public GT4HistOCR model (about 2.8%) by close to 40% relative.
- Finetuning LSH-4 on Camerarius editions reaches about 1.50% CER, against 2.98% when training from scratch on the same binary images without augmentation. The paper says this finetune is a few hours on CPU.
- Data augmentation helps training from scratch. It does not help once you are finetuning LSH-4. Binarization method still matters: Staatsbibliothek binarization beat the default in their comparison.
- Ground-truth rules include: standard Unicode, no PUA; keep vowel ligatures and split consonantal ones; collapse whitespace; map macrons to tildes; regularize quotes. CER is computed after the same standardization. Divergent comma-versus-virgula guidelines in GT4HistOCR showed up as fake errors.
- The largest remaining error class is whitespace (merged and split words), then lookalikes (e/c, n/u, ſ/f).

## Limitations

The transcription policy deletes macron-versus-tilde and a number of glyph distinctions. Those CERs are not a score for a linguistic edition that must keep macrons, dotted consonants, or italic. The engine is Calamari 2.1 with voter ensembles, not Kraken.

## Related

- [[entities/calamari-ocr]]
- [[concepts/ocr-evaluation-metrics]]
- [[concepts/diplomatic-ocr-target]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- <https://arxiv.org/pdf/2106.07881>
