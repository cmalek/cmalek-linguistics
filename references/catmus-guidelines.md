---
title: >-
    CATMuS Transcription Guidelines
category: references
tags: [transcription, medieval, ocr, diplomatic]
sources:
  - "url:https://catmus-guidelines.github.io/"
source_url: "https://catmus-guidelines.github.io/"
summary: >-
    Shared graphemic rules for medieval-to-modern Latin script. Keep abbreviation signs; do not expand them; do not record italic or bold.
provenance:
  extracted: 0.86
  inferred: 0.10
  ambiguous: 0.04
base_confidence: 0.60
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:45:00Z
updated: 2026-10-09T18:45:00Z
relationships:
  - target: "[[concepts/diplomatic-ocr-target]]"
    type: related_to
  - target: "[[concepts/ocr-character-inventory]]"
    type: related_to
---

# CATMuS Transcription Guidelines

[CATMuS guidelines](https://catmus-guidelines.github.io/) (Consistent Approaches to Transcribing Manuscripts). Cite as Pinche, Clérice, Chagué, Camps, Vlachou-Efstathiou, and others, 2023, hal-04346939. The site covers transcription only. It does not cover zone segmentation (see SegmOnto) or later normalization and abbreviation expansion.

## Key claims

- The method follows Robinson and Solopova: graphemic transcription keeps the sequence of letters and abbreviation signs, and reduces each letter shape to a standard alphabetic character.
- Abbreviations must be reproduced and must not be expanded. Expansion is a later task. The character table includes Tironian et `U+204A`, stroked p `U+A751`, and combining marks. Medieval tildes and macrons often share one combining tilde, because the guidelines refuse to multiply signs transcribers cannot agree on.
- Accents are transcribed when they appear. A dotted i is `i`, not `í`. A misaligned accent is placed on its letter, not left floating. Cedilla is combining `U+0327`.
- Letters use the modern Latin alphabet. Capitals stay capitals. Small caps become uppercase. Ligatures split into letters. Medieval `u`/`v` and `i`/`j` collapse to `u` and `i`. Modern documents keep the modern `u`/`v` distinction.
- “Stylistic elements (e.g., italics, bold) must not be transcribed.”
- Private Use Area characters, if used, must be documented in the project guidelines. Prefer MUFI characters that have public code points. [[references/mufi-character-recommendation]].

## Limitations

This is a shared training codec, not a facsimile of a printed linguistic edition. A grammar that uses italic for a cited form, a macron for length, and dotted `ċ` for palatalization loses those distinctions if you follow CATMuS literally. [[concepts/diplomatic-ocr-target]] treats CATMuS as the manuscript baseline and lists the extra rules a textbook needs. A 2026 comparison of CATMuS-trained and more-normalized models found similar recognition accuracy and treated the difference as an editorial choice of how much normalization sits in the output. ^[inferred]

## Related

- [[concepts/ocr-human-correction]]
- [[entities/kraken]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- <https://catmus-guidelines.github.io/>
- <https://catmus-guidelines.github.io/html/guidelines/en/generalites.html>
- <https://catmus-guidelines.github.io/html/guidelines/en/abbreviations.html>
- <https://catmus-guidelines.github.io/html/guidelines/en/letters_numbers.html>
