---
title: >-
    GlotOCR Bench
category: references
tags: [ocr, unicode, evaluation]
sources:
  - "url:https://arxiv.org/pdf/2604.12978"
source_url: "https://arxiv.org/pdf/2604.12978"
summary: >-
    2026 benchmark of OCR across 100+ Unicode scripts: frontier models cover a few dozen scripts and hallucinate familiar ones elsewhere.
provenance:
  extracted: 0.86
  inferred: 0.12
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
  - target: "[[concepts/diplomatic-ocr-target]]"
    type: related_to
---

# GlotOCR Bench

[arXiv:2604.12978](https://arxiv.org/pdf/2604.12978). Clean and degraded images rendered from real multilingual text with Google Fonts, HarfBuzz shaping, and FreeType, covering left-to-right and right-to-left scripts. Samples were checked by hand for correct rendering.

## Key claims

- Evaluation of document OCR has stayed on a small cluster of high- and mid-resource scripts.
- Most models they tried do well on fewer than ten scripts. The strongest frontier models fail to generalize past about thirty.
- Scores track how much of that script was in pretraining. The paper reads this as language-model memory doing as much work as visual recognition.
- Unfamiliar scripts produce noise or characters from a script the model already knows. The attractor scripts are Latin, Arabic, and Devanagari. Some substitutions follow script family (Coptic toward Greek, Syriac toward Arabic). Others are only distributional.

## Limitations

The images are rendered, so this is a character-coverage test, not a test of scholarly page layout, font subsetting, or Private Use Area glyphs. Latin-script dead languages with a few extra letters (thorn, wynn, macrons) are inside the “known script” bucket and are not the failure this paper measures. ^[inferred]

## Related

- [[concepts/ocr-character-inventory]]
- [[references/ocr-for-the-ipa]] — the same substitution pattern inside Latin, on IPA
- [[references/state-of-icelandic-ocr]] — þ/p and ð/d inside a known script
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- <https://arxiv.org/pdf/2604.12978>
