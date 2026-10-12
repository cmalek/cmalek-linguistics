---
title: >-
    Calamari OCR
category: entities
tags: [ocr, ipa, tools]
summary: >-
    Line-level neural OCR. In the 2026 IPA study it is the best open model after fine-tuning on synthetic phonetic text.
provenance:
  extracted: 0.84
  inferred: 0.12
  ambiguous: 0.04
base_confidence: 0.67
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:20:00Z
relationships:
  - target: "[[references/ocr-for-the-ipa]]"
    type: related_to
  - target: "[[concepts/ocr-character-inventory]]"
    type: implements
  - target: "[[entities/tesseract]]"
    type: related_to
sources:
  - "url:https://aclanthology.org/2026.eacl-short.19.pdf"
---

# Calamari OCR

[Calamari](https://github.com/Calamari-OCR/calamari) is a line OCR engine (CNN plus recurrent net) with GPU training. Wick et al. (2020) reported it ahead of Tesseract on their historical-print benchmarks, which is why the IPA paper starts there. The IPA paper starts from the `idiotikon` checkpoint, trained on the Schweizerisches Idiotikon, because that codec already includes many diacritics.

Off the shelf it is worse than Tesseract on IPA (CER about 52 on Japhug). After fine-tuning on the authors’ synthetic multilingual IPA set it is the best model in the study: CER 1.41 on Japhug, 0.20 on synthetic, 6.77 on unseen Kagayanen. Details and the training-data caveat (stress and tone stripped; rendered lines, not raw scans of whole pages) are on [[references/ocr-for-the-ipa]].

[[references/mixed-model-historical-ocr]] is the print-finetune result: a polyfont Calamari model near 1.7% CER on 29 unseen historical books, and a CPU finetune to about 1.50% CER against 2.98% from scratch. That ground truth maps macrons to tildes, so the number is not a macron score. Match the binarization the checkpoint saw.

Calamari does not segment pages. Pair it with a layout tool, and feed it line images cut from the OCR derivative, not a PDF text layer. See [[concepts/ocr-pipeline]] and [[concepts/pdf-text-layer-vs-ocr]].

## Related

- [[entities/tesseract]]
- [[entities/kraken]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- [[references/ocr-for-the-ipa]]
