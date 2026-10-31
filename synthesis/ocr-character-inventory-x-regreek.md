---
title: "OCR Character Inventory × regreek"
category: synthesis
tags: ["ocr", "unicode", "pdf", "linguistics"]
sources:
  - "concepts/ocr-character-inventory.md"
  - "entities/regreek.md"
  - "concepts/tounicode-cmap.md"
  - "concepts/pdf-text-layer-vs-ocr.md"
  - "entities/kraken.md"
  - "sources/kraken-6-recognition-codec-training.md"
  - "references/ocr-for-the-ipa.md"
  - "url:https://github.com/romain-girardi-eng/regreek"
summary: "A retained character label is not retained recognition skill; decoding attestation and OCR accuracy also require different validation."
provenance:
  extracted: 0.2
  inferred: 0.7
  ambiguous: 0.1
base_confidence: 0.55
lifecycle: draft
lifecycle_changed: "2026-10-28"
tier: supporting
created: 2026-10-28T17:28:59+00:00
updated: 2026-10-28T17:40:07+00:00
---

# OCR Character Inventory × regreek

## The Connection

[[concepts/ocr-character-inventory]] and [[entities/regreek]] both concern whether scholarly marks survive extraction. Research sharpens the shared lesson: having an output representation available is necessary, but it does not establish that the resulting characters match the witness. ^[inferred]

## Where They Co-occur

The original scan found three shared backlinks: [[concepts/tounicode-cmap]], [[concepts/pdf-text-layer-vs-ocr]], and [[entities/kraken]]. They distinguish recoverable legacy encodings from image recognition. This research does not change the current corpus’s image-first workflow.

## External Evidence

regreek’s README says unknown codes are preserved and flagged. Its Graeca evaluation reports 99.4% corpus attestation on 15,142 held-out tokens, while other tables have weaker validation. Attestation is not an aligned character-accuracy score. The evidence remains the project’s own report, not an independently reproduced benchmark. See [[entities/regreek]].

Kraken 6.0 warns that retaining codec labels with `union` does not prevent unlearning when fine-tuning omits them. Its guidance recommends `new`. See [[sources/kraken-6-recognition-codec-training]].

The EACL IPA study reports poor off-the-shelf performance associated with character-set mismatch and improvements from synthetic-data fine-tuning. That supports domain-specific training, rather than a guarantee from inventory size alone. See [[references/ocr-for-the-ipa]].

## Cross-cutting Insight

An audit needs three distinct checks: can the output represent the mark, did this conversion recover it correctly, and does the result preserve the distinctions required by the edition? A decoder may account for every input code using the wrong mapping. An OCR model may contain every required label while confusing their images. A plausible word can still carry the wrong accent or grammatical ending. ^[inferred]

For decoding, retain the encoding identity, unmapped-code report, and mapping evidence. For recognition, test held-out lines that actually contain rare marks. Compare both against the same transcription policy before comparing scores. This is a proposed evaluation design, not a measured improvement. ^[inferred]

## Tensions and Trade-offs

The earlier inventory page overstated `union` as a way to keep known letters. It preserves codec membership; adequate recognition still depends on training coverage and evaluation. The version-specific warning is now linked from that page. ^[inferred]

Neither a small aggregate CER nor a high word-attestation percentage establishes fidelity for the rare marks that matter to the scholar. The measures have different units and cannot be ranked as if interchangeable. ^[inferred]

## Strongest Objection

The proposed layered audit might find the same mistakes as ordinary careful proofreading, at greater cost. Documentation and benchmark results establish failure mechanisms but do not measure this audit’s additional benefit.

> test: on the same held-out pages, how many accent, quantity, and letter errors does the layered audit detect beyond a blinded readability-only review, and at what review time?

## Open Questions

- What extra rare-mark errors does this audit detect on the actual corpus, and how much correction time does it save or add?

## Related

- [[concepts/ocr-character-inventory]]
- [[entities/regreek]]
- [[synthesis/bosworth-toller-x-dictionary-build]]

## Sources

- [[entities/regreek]] — primary project README, including its validation limits
- [[sources/kraken-6-recognition-codec-training]] — versioned official documentation
- [[references/ocr-for-the-ipa]] — EACL 2026 paper
- [[concepts/pdf-text-layer-vs-ocr]] — scope of the current corpus workflow
