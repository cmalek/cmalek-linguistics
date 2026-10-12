---
title: >-
    olmOCR
category: references
tags: [ocr, markdown, evaluation]
sources:
  - "url:https://arxiv.org/abs/2502.18443"
source_url: "https://arxiv.org/abs/2502.18443"
summary: >-
    Allen AI PDF-to-markdown VLM and an English unit-test bench. Useful for layout linearization; it does not score rare letters.
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
  - target: "[[concepts/scholarly-markdown-limits]]"
    type: related_to
  - target: "[[entities/marker-pdf]]"
    type: related_to
  - target: "[[entities/docling]]"
    type: related_to
---

# olmOCR

Allen Institute for AI. Paper: [arXiv:2502.18443](https://arxiv.org/abs/2502.18443). Bench dataset: [allenai/olmOCR-bench](https://huggingface.co/datasets/allenai/olmOCR-bench). Later system cards (olmOCR-2) appear in [[references/reading-or-guessing-vlm-ocr]].

The system prompts a vision-language model, originally Qwen2-VL class, to linearize a PDF page to markdown. “Anchored” runs pass location hints from the PDF text layer into the prompt.

## Key claims

- olmOCR-Bench is 1,403 PDFs and 7,010 pass/fail tests: a short span must appear, a span must be absent, local reading order, a table adjacency, a formula, headers and footers, tiny text, multi-column, old scans, old math. Early anchored olmOCR overall is about 77; later Marker documentation reports Chandra hosted at 85.8 and Marker balanced at 76.0 on the same style of overall score.
- Non-English pages were filtered out. A baseline test fails the page if the output contains CJK or emoji, except a few hand-flagged pages.
- Before scoring, Unicode is NFC-normalized, and hyphen, quote, and apostrophe variants are folded to ASCII `-`, `"`, and `'`. A macron-vs-no-macron difference would still fail a presence test. A hyphen-variant difference would not. ^[inferred]
- Old scans in the bench are Library of Congress letters and typescripts with crowd transcriptions, plus checks that headers and footers stay out of the text.
- LlamaIndex’s review of the bench: tables that Gemini Flash could not parse consistently were left out; handwriting, forms, and foreign languages were excluded; table tests check a neighbour relation, not spans or completeness; reading-order tests avoid captions, footnotes, and floats. Exact string match also fails on a harmless space or comma.

## Limitations

A high olmOCR-Bench number is evidence about English linearization. It is not evidence about thorn, eth, macrons, dotted consonants, or IPA. Header/footer removal, which several converters treat as a feature, deletes running titles and signatures that an edition may need.

## Related

- [[concepts/scholarly-markdown-limits]]
- [[entities/marker-pdf]] and [[entities/docling]] — systems scored on this bench
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- <https://arxiv.org/abs/2502.18443>
- <https://huggingface.co/datasets/allenai/olmOCR-bench>
- <https://www.llamaindex.ai/blog/olmocr-bench-review-insights-and-pitfalls-on-an-ocr-benchmark>
