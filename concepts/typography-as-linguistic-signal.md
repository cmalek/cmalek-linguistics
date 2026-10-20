---
title: >-
    Typography as Linguistic Signal
category: concepts
tags: [typography, ocr, linguistics]
summary: >-
    In grammars and editions, italic, bold, underline, and small caps carry linguistic meaning. Capture the style with the characters.
provenance:
  extracted: 0.68
  inferred: 0.28
  ambiguous: 0.04
base_confidence: 0.73
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:20:00Z
relationships:
  - target: "[[concepts/scholarly-markdown-limits]]"
    type: related_to
  - target: "[[entities/pymupdf]]"
    type: uses
  - target: "[[concepts/pdf-text-layer-vs-ocr]]"
    type: related_to
sources:
  - "url:https://pymupdf.readthedocs.io/en/latest/textpage.html"
  - "url:https://aclanthology.org/2022.amta-upg.27.pdf"
  - "url:https://github.com/tex-tar/tex-tar"
---

# Typography as Linguistic Signal

A grammar uses type style as part of the notation. Italic often marks a cited word or a lemma. Bold often marks a headword. Underline often marks a manuscript reading or emphasis the editor could not set in italic. Small caps often mark a siglum or an expanded abbreviation. Superscripts mark notes, and in phonetics they mark aspiration, tone, and secondary articulation. Losing the style loses the analysis even when every letter is right.

## Key ideas

- On a born-digital PDF, style is metadata. [[entities/pymupdf]] `get_text("dict")` spans expose `font`, `size`, `color`, and `flags`. Documented flag bits: 0 superscript (detected, not a font bit), 1 italic, 2 serif, 3 monospace, 4 bold. From v1.25.2, `char_flags` adds strikeout (bit 0), underline (bit 1), synthetic, filled, stroked, and clipped. The same page says font programs often store those style bits incorrectly, so the font name (`Bold`, `Italic`, `Oblique`) has to be checked as well. The documentation’s sample test ANDs the bold and italic constants together, which does not mean “both styles.” Test each bit on its own. ^[inferred]
- Underline is often a vector drawn under the glyphs, not a font style. Pairing a horizontal line with the text baseline is the fallback when `char_flags` has no underline bit. Synthetic italic is sometimes a sheared text matrix rather than an italic font.
- OCR of a raster throws this metadata away. The 2022 ARLIS note on OCR and translation (AMTA) says Tesseract’s hOCR gives boxes and does not attempt bold or italic, which matters for dictionaries. They inferred headings from box height. TexTAR is a later model that labels bold, italic, underline, and strikeout on word crops with surrounding context, because a table rule looks like an underline.
- Do not collapse styles into one “emphasis” mark before you have a policy for that book. Store the observed style. Map it to linguistic roles in a second step. ^[inferred]
- On a scan, line OCR returns a string and does not return bold or italic. [[references/catmus-guidelines]] tell transcribers to omit italic and bold. A linguistic edition that needs them keeps a style attribute beside the diplomatic string. Putting asterisks into the ground truth makes style part of the character error rate. [[concepts/ocr-human-correction]]. TexTAR is a separate model that labels bold, italic, underline, and strikeout on word crops.
- [[entities/docling]] can serialize bold and italic to markdown and underline to HTML when it detected them. On these PDFs the text layer is ignored, so that detection has to come from the image. See [[concepts/pdf-text-layer-vs-ocr]].
- OpenType features in [[entities/junicode]] are a special case. The medieval shape may be a feature on an ordinary letter. The feature is typography. The letter is the character. Keep both if the PDF still has both. If the PDF stored only the substituted glyph, you have a character-identity problem, not a bold/italic problem. See [[concepts/tounicode-cmap]].

## Related

- [[synthesis/tounicode-cmap-x-typography-as-linguistic-signal|ToUnicode CMap × Typography as Linguistic Signal]] — synthesis
- [[concepts/scholarly-markdown-limits]]
- [[skills/linguistic-pdf-to-markdown]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- [PyMuPDF TextPage](https://pymupdf.readthedocs.io/en/latest/textpage.html)
- [You’ve translated it, now what? (AMTA 2022)](https://aclanthology.org/2022.amta-upg.27.pdf)
- [TexTAR](https://github.com/tex-tar/tex-tar)
- [[references/junicode-manual]]
