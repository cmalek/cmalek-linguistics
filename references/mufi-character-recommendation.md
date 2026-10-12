---
title: >-
    MUFI Character Recommendation
category: references
tags: [unicode, medieval, typography]
sources:
  - "url:https://mufi.info/projects/mufi/pdfs/MUFI%20v4.0%20chart.pdf"
source_url: "https://mufi.info/projects/mufi/pdfs/MUFI%20v4.0%20chart.pdf"
summary: >-
    Medieval Unicode Font Initiative v4 code chart: standard code points for medieval letters, and a warning against Private Use Area text.
provenance:
  extracted: 0.90
  inferred: 0.08
  ambiguous: 0.02
base_confidence: 0.62
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:20:00Z
relationships:
  - target: "[[concepts/ocr-character-inventory]]"
    type: related_to
  - target: "[[entities/junicode]]"
    type: related_to
  - target: "[[concepts/tounicode-cmap]]"
    type: related_to
---

# MUFI Character Recommendation

Medieval Unicode Font Initiative, character recommendation version 4.0 (2015 chart). [Alphabetical chart PDF](https://mufi.info/projects/mufi/pdfs/MUFI%20v4.0%20chart.pdf). Proposals still under review: [mufi.info proposals](https://mufi.info/q?p=mufi/proposals).

## Key claims

- Durable text should use Unicode code points, with markup or entities where a character has no standard point. Private Use Area (PUA) glyphs display correctly only in a MUFI-compliant font. The same PUA slot can mean different things in two fonts.
- If Unicode later encodes a PUA character, MUFI moves it. Documents that stored the old PUA point break. Keep the font file, and embed fonts in any PDF kept as a visual record.
- Code points that matter for Old and Middle English editions, from the v4 chart: Þ/þ `U+00DE`/`U+00FE`, Ð/ð `U+00D0`/`U+00F0`, æ/Æ `U+00E6`/`U+00C6`, ǣ/Ǣ `U+01E3`/`U+01E2`, wynn ƿ `U+01BF`, yogh ȝ/Ȝ `U+021D`/`U+021C`. Insular letterforms that Unicode has since encoded should follow the current point, not an old PUA slot.
- Proposed characters (double thorn, double wynn, and similar) are given temporary PUA-B points and “should not be used for production fonts or published works.”
- Combining marks already in Unicode cover many stacked diacritics: macron `U+0304`, acute `U+0301`, grave `U+0300`, tilde `U+0303`, diaeresis `U+0308`, dot above `U+0307`, dot below `U+0323`, inverted breve `U+0311`, double macron `U+035E`, double breve `U+035D`. Precomposed characters exist for some stacks (ǖ `U+01D6`) and not for others.

## Limitations

The recommendation is an encoding policy, not an OCR model. A PDF can still draw a MUFI glyph while its text layer stores a PUA point, a Latin lookalike, or nothing useful. See [[concepts/tounicode-cmap]].

## Related

- [[entities/junicode]] — a font that implements the recommendation and also offers a non-PUA encoding path
- [[concepts/ocr-character-inventory]]
- [[concepts/old-english-pronunciation]] — þ, ð, æ, wynn, macrons, dotted ċ/ġ
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- <https://mufi.info/projects/mufi/pdfs/MUFI%20v4.0%20chart.pdf>
- <https://mufi.info/q?p=mufi/proposals>
