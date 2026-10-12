---
title: >-
    regreek
category: entities
tags: [greek, pdf, unicode, tools]
summary: >-
    Deterministic decoder from legacy Greek font encodings to Unicode. It repairs a text layer and refuses to invent characters.
provenance:
  extracted: 0.86
  inferred: 0.12
  ambiguous: 0.02
base_confidence: 0.55
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:20:00Z
relationships:
  - target: "[[concepts/tounicode-cmap]]"
    type: implements
  - target: "[[entities/kraken]]"
    type: related_to
sources:
  - "url:https://github.com/romain-girardi-eng/regreek"
---

# regreek

[regreek](https://github.com/romain-girardi-eng/regreek) turns pre-Unicode Greek font encodings (Graeca, SPIonic, Bwgrkl, Odyssea, GreekKeys, and others) into NFC polytonic Unicode. The PDF looks like Greek. `pdftotext`, PyMuPDF, and pdfminer return Latin keystrokes, because the font’s ToUnicode map says the glyphs are Latin.

Decoding is a table plus mark-attachment rules (breathings, accents, iota subscript, diaeresis, and the per-font order of those marks). There is no language model. An input character is mapped or it is not. The tool records per-character provenance. Subset prefixes (`FH+Gra…`) are stripped before the font is identified. Diacritics that the PDF stored on the following line are a known hazard.

The project is explicit that this is not OCR. Scanned polytonic pages need a recognizer. They name Kraken with the Ciaconna model for that, and they note that OCR can invent a character, which this decoder will not.

The same pattern applies to other legacy scholarly fonts (MUFI PUA, old phonetic fonts). The Greek tables do not transfer. The method does: glyph name or keystroke to a documented Unicode string. See [[concepts/tounicode-cmap]].

## Related

- [[entities/pymupdf]]
- [[references/reading-or-guessing-vlm-ocr]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- <https://github.com/romain-girardi-eng/regreek>
