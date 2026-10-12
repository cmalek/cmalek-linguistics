---
title: >-
    Optical Character Recognition for the International Phonetic Alphabet
category: references
tags: [ocr, ipa, linguistics, evaluation]
sources:
  - "url:https://aclanthology.org/2026.eacl-short.19.pdf"
source_url: "https://aclanthology.org/2026.eacl-short.19.pdf"
summary: >-
    EACL 2026 short paper: off-the-shelf OCR fails on IPA; fine-tuned Calamari on synthetic lines drops CER under 2%.
provenance:
  extracted: 0.88
  inferred: 0.10
  ambiguous: 0.02
base_confidence: 0.67
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:20:00Z
relationships:
  - target: "[[concepts/ocr-character-inventory]]"
    type: related_to
  - target: "[[entities/tesseract]]"
    type: uses
  - target: "[[entities/calamari-ocr]]"
    type: uses
  - target: "[[concepts/diplomatic-ocr-target]]"
    type: related_to
---

# Optical Character Recognition for the International Phonetic Alphabet

Shu Okabe, Dejvi Zelo, and Alexander Fraser, EACL 2026 short papers, pp. 265–273. [PDF](https://aclanthology.org/2026.eacl-short.19.pdf). Code and models: [TUM-NLP/ocr-ipa](https://github.com/TUM-NLP/ocr-ipa).

Line-level OCR of IPA in grammar-book style images. Compares Tesseract (`eng` and `lat`), Calamari (Schweizerisches Idiotikon checkpoint), and Qwen2.5-VL-7B, each off the shelf and after fine-tuning.

## Key claims

- Grammar-book scans are a real source of linguistic data (ODIN, IMTVault), and earlier OCR of those scans was noisy.
- Zero-shot character error rate is poor because the recognizer’s character set does not include the IPA symbols. Reported CER: Tesseract English 33.94 (Japhug) / 36.44 (synthetic); Tesseract Latin 32.46 / 34.02; Calamari 52.36 / 57.12; Qwen2.5-VL-7B 28.36 on Japhug and 35.42 on the distilled synthetic set. The Latin model’s larger diacritic set helps only a little.
- Models then substitute the nearest character they already know.
- Fine-tuning on one grammar (Japhug, Charis SIL, about 13k chunks) gives the best in-domain score and the worst transfer. Tesseract Latin fine-tuned on Japhug: CER 2.42 on Japhug and 43.08 on the synthetic set.
- Fine-tuning on a large synthetic set generalizes better. The synthetic set is Wikipron IPA for 307 languages, turned into pseudo-sentences, rendered in Charis SIL, Doulos SIL, Gentium, Andika, and Brill, then corrupted. Best model: Calamari trained on that set, CER 1.41 and WER 6.28 on Japhug, CER 0.20 and WER 2.45 on synthetic. On unseen Kagayanen: CER 6.77, WER 34.07. Qwen fine-tuned on a distilled half of the synthetic data: CER 2.89 on Japhug, 0.12 on the distilled test, 8.65 on Kagayanen.
- Stress marks, syllable boundaries, and tone marks were removed from the synthetic data before training.

## Limitations

Images are rendered and then noised. They are line crops, so the paper does not test page layout, tables, or footnotes. Qwen numbers are not directly comparable to the Tesseract and Calamari table because the synthetic set was distilled and the splits differ. The authors say the computational cost of the vision-language model is much higher.

## Related

- [[concepts/ocr-character-inventory]] — why the codec has to list every mark before training
- [[entities/calamari-ocr]] and [[entities/tesseract]] — the two line recognizers
- [[concepts/phonetics-and-phonology]] — what the IPA inventory is for
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- <https://aclanthology.org/2026.eacl-short.19.pdf>
