---
title: >-
    ToUnicode CMap
category: concepts
tags: [pdf, unicode, fonts]
summary: >-
    The ToUnicode map tells extractors which character a PDF glyph is. Scholarly fonts often map thorn, macrons, and Greek to the wrong code.
provenance:
  extracted: 0.72
  inferred: 0.22
  ambiguous: 0.06
base_confidence: 0.72
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:20:00Z
relationships:
  - target: "[[concepts/pdf-text-layer-vs-ocr]]"
    type: related_to
  - target: "[[entities/junicode]]"
    type: related_to
  - target: "[[entities/regreek]]"
    type: uses
  - target: "[[references/mufi-character-recommendation]]"
    type: related_to
sources:
  - "url:https://github.com/romain-girardi-eng/regreek"
  - "url:https://github.com/piotrgulbis/pdf-cmap-fixer"
  - "url:https://github.com/OpenPecha/pdf-cmap-fix"
  - "url:https://ctan.math.illinois.edu/fonts/junicode/doc/JunicodeManual.pdf"
---

# ToUnicode CMap

Inside a PDF, text is a sequence of character codes for a font, not a sequence of Unicode scalars. A `/ToUnicode` CMap translates those codes into Unicode so that copy, search, and `pdftotext` return letters. If the map is missing or points at the wrong scalars, every extractor returns the same wrong string. The page still draws the right shapes, because drawing uses glyph ids, not the Unicode map.

## Key ideas

- Legacy Greek fonts (Graeca, SPIonic, GreekKeys, and others, roughly 1985–2005) store polytonic Greek as Latin keystrokes. [[entities/regreek]] decodes that keystroke stream with a per-font table. It does not guess. A character with no evidenced mapping is left unmapped. The project states that scanned pages still need OCR, and that OCR output cannot carry the same “never invent a character” guarantee.
- Subset font names in the PDF look like `ABCDEF+Junicode`. Matching them to a known font means stripping the prefix. Tools that rebuild CMaps from embedded fonts do this: [pdf-cmap-fixer](https://github.com/piotrgulbis/pdf-cmap-fixer) reads PostScript glyph names (`thorn`, `uni00FE`, `a.sc`); [pdf-cmap-fix](https://github.com/OpenPecha/pdf-cmap-fix) ships GID, glyph-name, and outline-fingerprint lookups, including Tibetan stacks decomposed from GSUB ligatures.
- Glyphs named `uniE0xx` or similar sit in the Private Use Area. [[references/mufi-character-recommendation]] warns that those points are not interchangeable across fonts. pdf-cmap-fixer renders them to a contact sheet so a person can name them once per font.
- [[entities/junicode]] prefers the opposite authoring practice: store `a` plus an OpenType feature, and let the layout engine draw the medieval glyph. A PDF that followed that advice extracts as plain Latin. A PDF that embedded the substituted glyph or a MUFI PUA point extracts as something else. Both can look identical on the page. ^[inferred]
- Ligatures and line-end diacritics split one letter across two codes or two lines. regreek documents a real case where a Greek diacritic was stored on the next line. Any repair has to run before line joining.
- After a repair, check the character inventory, not a sample sentence of ordinary English. See [[concepts/ocr-character-inventory]].

## Related

- [[concepts/pdf-text-layer-vs-ocr]]
- [[entities/pymupdf]] — reads whatever the CMap says
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- [regreek](https://github.com/romain-girardi-eng/regreek)
- [pdf-cmap-fixer](https://github.com/piotrgulbis/pdf-cmap-fixer)
- [pdf-cmap-fix](https://github.com/OpenPecha/pdf-cmap-fix)
- [[references/junicode-manual]]
- [[references/mufi-character-recommendation]]
