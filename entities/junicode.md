---
title: >-
    Junicode
category: entities
tags: [fonts, unicode, medieval, old-english]
summary: >-
    A MUFI-complete medievalist font. Best practice stores plain Unicode and draws rare shapes with OpenType, which changes what a PDF text layer contains.
provenance:
  extracted: 0.84
  inferred: 0.14
  ambiguous: 0.02
base_confidence: 0.62
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:20:00Z
relationships:
  - target: "[[references/junicode-manual]]"
    type: derived_from
  - target: "[[references/mufi-character-recommendation]]"
    type: implements
  - target: "[[concepts/tounicode-cmap]]"
    type: related_to
sources:
  - "url:https://ctan.math.illinois.edu/fonts/junicode/doc/JunicodeManual.pdf"
---

# Junicode

[Junicode](https://ctan.math.illinois.edu/fonts/junicode/doc/JunicodeManual.pdf), designed by Peter S. Baker, is the usual font for Old English and other medieval scholarship. Version 2 covers the [[references/mufi-character-recommendation|MUFI]] v4 repertoire: thorn, eth, wynn, yogh, insular forms, and the combining marks those editions stack.

The manual’s encoding advice is the part that matters for extraction. Underlying text should be ordinary Unicode. Medieval shapes should be OpenType features (`cv02`, `ss01` for alternate thorn and eth, and the rest of the feature reference). PUA code points still display, and they fail search, accessibility, and interchange. A PDF from a publisher may have followed that advice, embedded a PUA glyph, or subsetted a precomposed glyph with a bad ToUnicode map. Those three files can look the same. [[entities/pymupdf]] will show which one you have.

SIL fonts (Charis, Doulos, Gentium, Andika) and Brill are the parallel set for IPA. [[references/ocr-for-the-ipa]] uses them as the rendering fonts for synthetic training lines. They do not solve a broken text layer by themselves.

## Related

- [[concepts/old-english-pronunciation]]
- [[concepts/ocr-character-inventory]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- [[references/junicode-manual]]
- [[references/mufi-character-recommendation]]
