---
title: "Crist 2011: processing bilingual print dictionaries"
category: references
tags: ["lexicography", "nlp", "provenance"]
relationships:
  - target: "[[entities/bosworth-toller]]"
    type: related_to
  - target: "[[projects/wyrdcraeft/wyrdcraeft]]"
    type: related_to
sources:
  - "url:https://www.sean-crist.com/all/crist_dictionaries_20111210.pdf"
source_url: "https://www.sean-crist.com/all/crist_dictionaries_20111210.pdf"
summary: "Crist separates acquisition, tagging, parsing, and validation; dictionary markup errors and textual errors require different checks."
provenance:
  extracted: 0.85
  inferred: 0.10
  ambiguous: 0.05
base_confidence: 0.55
lifecycle: draft
lifecycle_changed: "2026-10-28"
tier: supporting
created: 2026-10-28T17:40:07+00:00
updated: 2026-10-28T17:40:07+00:00
---


# Crist 2011: processing bilingual print dictionaries

Sean Crist, *Processing the Text of Bilingual Print Dictionaries*, unpublished draft dated in the file URL to 10 December 2011.

## Findings

Sections 3.3.2 and 3.3.8 (PDF pp. 27 and 29) distinguish errors in the original dictionary from digitization errors and propose field-specific validation: permitted characters, abbreviation inventories, numbering, balanced delimiters, and external resources. Section 1.3 reports [[entities/bosworth-toller|Bosworth-Toller]] token tagging; the evaluation concerns field labels, not lexical truth or transcription accuracy.

## Limits

The paper is an unpublished draft. Its checks identify candidates for correction; corpus absence is a reason for inspection, not proof that a rare form is wrong. It does not evaluate [[projects/wyrdcraeft/wyrdcraeft|wyrdcraeft]] or establish that its merges preserve every distinction.

## Related

- [[synthesis/bosworth-toller-x-dictionary-build]]
- [[synthesis/ocr-character-inventory-x-regreek]]
- [[projects/wyrdcraeft/concepts/dictionary-build]]

## Sources

- [External source 1](https://www.sean-crist.com/all/crist_dictionaries_20111210.pdf)
