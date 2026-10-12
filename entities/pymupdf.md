---
title: >-
    PyMuPDF
category: entities
tags: [pdf, python, tools]
summary: >-
    Python binding to MuPDF. Reads a PDF text layer with font, size, bold, italic, and per-character underline flags.
provenance:
  extracted: 0.82
  inferred: 0.14
  ambiguous: 0.04
base_confidence: 0.60
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:20:00Z
relationships:
  - target: "[[concepts/pdf-text-layer-vs-ocr]]"
    type: implements
  - target: "[[concepts/typography-as-linguistic-signal]]"
    type: implements
sources:
  - "url:https://pymupdf.readthedocs.io/en/latest/textpage.html"
---

# PyMuPDF

[PyMuPDF](https://pymupdf.readthedocs.io/en/latest/textpage.html) (`import pymupdf`) extracts text from a PDF through MuPDF. It does not OCR.

## What it gives you

- `page.get_text("dict")` returns blocks, lines, and spans. Each span has `text`, `font`, `size`, `color`, `flags`, and `bbox`.
- `page.get_text("rawdict")` adds every character (`origin`, `bbox`, the Unicode scalar). Use it when a span mixes styles or when a diacritic might be its own glyph.
- `page.get_text("html")` and `"xml"` carry formatting. XML is per character and has no images. HTML tries to keep appearance and does not recreate the page exactly.
- Flag bits are documented on [[concepts/typography-as-linguistic-signal]]. Font programs often contain wrong bold/italic bits. `char_flags` underline and strikeout exist from v1.25.2.
- `search_for` casefolds ASCII only. Searching `Ä` does not match `ä`.

## What it does not fix

The Unicode string is whatever the `/ToUnicode` map says. Wrong maps come out wrong in every output mode. See [[concepts/tounicode-cmap]]. Sort-by-coordinate reading order is a heuristic. Footnotes, floats, and two-column editions still need region labels before you emit markdown. See [[concepts/scholarly-markdown-limits]].

## Related

- [[skills/linguistic-pdf-to-markdown]]
- [[entities/docling]] — uses a text layer when one exists, and adds layout models
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- <https://pymupdf.readthedocs.io/en/latest/textpage.html>
