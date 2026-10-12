---
title: >-
    Error Patterns in Historical OCR
category: references
tags: [ocr, evaluation, historical-text]
sources:
  - "url:https://arxiv.org/pdf/2602.14524"
source_url: "https://arxiv.org/pdf/2602.14524"
summary: >-
    Helsinki 2026: on 18th-century English lines, Qwen has lower CER than TrOCR and also silently modernizes spelling; TrOCR keeps the spelling and cascades.
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
  - target: "[[concepts/diplomatic-ocr-target]]"
    type: related_to
  - target: "[[references/reading-or-guessing-vlm-ocr]]"
    type: related_to
---

# Error Patterns in Historical OCR

Ari Vesalainen, Eetu Mäkelä, Laura Ruotsalainen, and Mikko Tolonen (University of Helsinki). [arXiv:2602.14524](https://arxiv.org/pdf/2602.14524).

Line-level comparison of TrOCR and Qwen on eighteenth-century printed English, scored against a diplomatic transcription.

## Key claims

- The target keeps the printed forms: long s, ligatures, diacritics, punctuation, and capitalization. It does not modernize spelling, expand abbreviations, or regularize lexis.
- The only normalization applied to both the reference and the hypothesis is technical: collapse whitespace, strip ends, map Unicode dashes to ASCII hyphen, collapse repeated hyphens. CER is then a grapheme error, not a dash-encoding error.
- Qwen has lower CER and WER and handles degraded lines better. It also selectively regularizes orthography, so a historically meaningful spelling can change while the string still looks fluent.
- TrOCR keeps orthography more consistently and is more likely to cascade errors along a line.
- Similar CER therefore does not mean similar correction cost. A local visual mistake is easier to spot than a plausible respelling.

A companion discussion of the same risk, aimed at post-correction rather than first-pass OCR, is Emanuel Boros, [Can LLMs Correct Historical OCR Without Rewriting History?](https://huggingface.co/blog/emanuelaboros/can-llms-correct-historical-ocr-without-rewriting) (2026). That note separates improved, neutral, unfaithful (meaning kept, historical form changed), harmful, and policy-dependent edits. Generative correctors may modernize spelling, alter rare names, drop uncertain passages, or insert text the page does not support.

## Limitations

The print is eighteenth-century English, not Old English or a linguistic apparatus. The architectural contrast (encoder–decoder OCR vs open generation) matches [[references/reading-or-guessing-vlm-ocr]] on Greek and Arabic. ^[inferred]

## Related

- [[concepts/diplomatic-ocr-target]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- <https://arxiv.org/pdf/2602.14524>
- <https://huggingface.co/blog/emanuelaboros/can-llms-correct-historical-ocr-without-rewriting>
