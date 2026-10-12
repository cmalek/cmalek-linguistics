---
title: >-
    OCR Evaluation Metrics
category: concepts
tags: [ocr, evaluation, cer]
summary: >-
    Character error rate on held-out lines, plus a confusion list for the rare marks. One overall CER hides a dropped macron.
provenance:
  extracted: 0.74
  inferred: 0.20
  ambiguous: 0.06
base_confidence: 0.76
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:45:00Z
updated: 2026-10-09T18:45:00Z
relationships:
  - target: "[[concepts/diplomatic-ocr-target]]"
    type: uses
  - target: "[[concepts/ocr-pipeline]]"
    type: related_to
sources:
  - "url:https://escriptorium.readthedocs.io/en/latest/train/"
  - "url:https://arxiv.org/pdf/2106.07881"
  - "url:https://export.arxiv.org/pdf/2301.05935v2.pdf"
---

# OCR Evaluation Metrics

Score the diplomatic string you asked the model to produce. Apply the same normalization to the hypothesis and the reference, and no other normalization.

## Character error rate

CER is the Levenshtein distance (insertions, deletions, substitutions) divided by the number of characters in the reference. [[entities/escriptorium]] reports the complement as accuracy: 90% accuracy is 10% CER. Their worked example is 330 errors in 3,330 characters = 9.90% CER.

Hold out about 10% of corrected lines, or whole pages, and never train on them. [[references/ocr-of-historical-printings]] (Ocrocis) and Transkribus both use that split. Early stopping in [[references/mixed-model-historical-ocr]] watches validation CER and stops after five epochs without improvement.

A single CER is not enough:

- Report a confusion list for the inventory: þ/p, ð/d, æ/ae, macron present or absent, dot present or absent, long s/f. Reul’s tables show the bulk of remaining errors can be whitespace, comma/virgula, and lookalike pairs (e/c, n/u, ſ/f). A 2% CER that is mostly spaces is a different problem from a 2% CER that drops macrons.
- Length-weight the score if you average pages. A short title page should not count as much as a full text page. ^[inferred]
- WER treats every wrong word as one error. Historical spelling and inflection make many one-character mistakes into other real words, so WER overstates the correction job and also hides which character failed. [[references/state-of-icelandic-ocr]].

## Do not mix stages into one number

Vidal, Toselli, and colleagues argue that page-level word error mixes recognition with reading order. They define a bag-of-words WER that ignores order, and a separate reading-order distance. Use line CER for the recognizer. Use a reading-order check for the segmenter. A perfect line model still fails a page if the apparatus is read as body text.

## Policy identity

[[references/mixed-model-historical-ocr]] standardizes OCR output the same way as the ground truth before computing CER. If the policy maps a macron to a tilde, both sides must do that, and the published CER no longer measures macron fidelity. [[concepts/diplomatic-ocr-target]] says to keep that policy written down. [[references/olmocr]] folds hyphens and quotes before scoring; copying that fold will hide a punctuation distinction you may care about.

Vision-language CER has extra failure modes that a line recognizer does not: repetition, markup dumped into the text, and modernization. [[references/historical-ocr-error-patterns]] and the 2025 LM4DH framework treat temporal conflation and anachronistic insertions as separate from edit distance.

## Practical gates

On a book you are about to accept:

- Held-out line CER, with the confusion list.
- One paradigm table checked cell by cell.
- One footnote still tied to its anchor.
- A page that looks fluent, audited for missing diacritics.

Kraken’s test command writes a difference report against a manifest of held-out lines. eScriptorium shows accuracy per training epoch. Download the epoch with the best validation accuracy, not the last epoch.

## Related

- [[concepts/ocr-human-correction]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- [eScriptorium training](https://escriptorium.readthedocs.io/en/latest/train/)
- [[references/mixed-model-historical-ocr]]
- [[references/ocr-of-historical-printings]]
- [End-to-end page-level HTR assessment](https://export.arxiv.org/pdf/2301.05935v2.pdf)
