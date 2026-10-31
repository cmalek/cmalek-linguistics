---
title: "Kraken 6.0: codec resizing and fine-tuning"
category: references
tags: ["ocr", "unicode", "evaluation"]
sources:
  - "url:https://kraken.re/6.0.0/training/rectrain.html"
source_url: "https://kraken.re/6.0.0/training/rectrain.html"
summary: "Kraken distinguishes keeping output labels from retaining learned recognition; its fine-tuning guidance recommends new rather than union."
provenance:
  extracted: 0.85
  inferred: 0.10
  ambiguous: 0.05
base_confidence: 0.61
lifecycle: draft
lifecycle_changed: "2026-10-28"
tier: supporting
created: 2026-10-28T17:40:07+00:00
updated: 2026-10-28T17:40:07+00:00
---

# Kraken 6.0: codec resizing and fine-tuning

## Findings

Version 6.0: `union` retains codec labels; `new` matches the training inventory. The documentation recommends `new`, warning that absent labels are unlearned during fine-tuning.

## Limits

Label availability does not ensure accuracy. ^[inferred] No local training was run; other releases were not verified.

## Related

- [[synthesis/ocr-character-inventory-x-regreek]]
- [[concepts/ocr-character-inventory]]
- [[entities/kraken]]

## Sources

- [External source 1](https://kraken.re/6.0.0/training/rectrain.html)
