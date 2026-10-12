---
title: >-
    Junicode Manual and Feature Reference
category: references
tags: [unicode, fonts, medieval, typography]
sources:
  - "url:https://ctan.math.illinois.edu/fonts/junicode/doc/JunicodeManual.pdf"
source_url: "https://ctan.math.illinois.edu/fonts/junicode/doc/JunicodeManual.pdf"
summary: >-
    Junicode 2 manual: medieval glyphs should be OpenType features on plain Unicode, because PUA text does not survive search or extraction.
provenance:
  extracted: 0.86
  inferred: 0.12
  ambiguous: 0.02
base_confidence: 0.60
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:20:00Z
relationships:
  - target: "[[entities/junicode]]"
    type: related_to
  - target: "[[references/mufi-character-recommendation]]"
    type: implements
  - target: "[[concepts/tounicode-cmap]]"
    type: related_to
---

# Junicode Manual and Feature Reference

Peter S. Baker’s Junicode manual on CTAN, [JunicodeManual.pdf](https://ctan.math.illinois.edu/fonts/junicode/doc/JunicodeManual.pdf), and the [OpenType feature reference](https://mirrors.dotsrc.org/mirrors/pub/pub/ctan/fonts/junicode/doc/Feature_Reference.tex). Junicode 2 contains the [[references/mufi-character-recommendation|MUFI]] v4 character set.

## Key claims

- The font has two jobs: expose MUFI characters, and keep the underlying text searchable. The manual splits a document into an underlying text and a displayed text. The underlying text should be the plain letter (`U+0061` for a) plus markup. A layout engine applies an OpenType feature such as `cv02[5]` to draw the medieval shape. Search, screen readers, and PDF text extraction then see the plain letter.
- PUA code points still work as input. The manual treats them as the worse path for anything that must remain text.
- `ss01` selects alternate thorn and eth shapes. Those alternates are presentation. The character identity stays thorn or eth when the feature path is used.
- Stylistic shapes (insular letters, enlarged thorn, combining-mark placement) are features. A PDF producer that embeds the already-substituted glyph, or a PUA glyph, stores a different string than the one the reader sees. ^[inferred]

## Limitations

The manual describes how to author text. It does not say what a given publisher’s PDF actually embedded. Extraction has to inspect that file. See [[concepts/tounicode-cmap]] and [[entities/pymupdf]].

## Related

- [[entities/junicode]]
- [[concepts/typography-as-linguistic-signal]] — the feature is the style; the character is the letter
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- <https://ctan.math.illinois.edu/fonts/junicode/doc/JunicodeManual.pdf>
- <https://mirrors.dotsrc.org/mirrors/pub/pub/ctan/fonts/junicode/doc/Feature_Reference.tex>
