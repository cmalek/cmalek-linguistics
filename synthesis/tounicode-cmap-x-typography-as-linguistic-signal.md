---
title: >-
    ToUnicode CMap × Typography as Linguistic Signal
category: synthesis
tags: [pdf, unicode, typography, linguistics]
relationships:
  - target: "[[concepts/tounicode-cmap]]"
    type: derived_from
  - target: "[[concepts/typography-as-linguistic-signal]]"
    type: derived_from
  - target: "[[entities/junicode]]"
    type: related_to
sources:
  - "[[concepts/tounicode-cmap]]"
  - "[[concepts/typography-as-linguistic-signal]]"
  - "[[concepts/pdf-text-layer-vs-ocr]]"
  - "[[entities/pymupdf]]"
summary: >-
    A PDF stores character identity and style in separate channels; repairing the first can destroy the second, notably when a small-caps glyph is remapped to a plain letter.
provenance:
  extracted: 0.20
  inferred: 0.70
  ambiguous: 0.10
base_confidence: 0.72
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T19:00:00Z
updated: 2026-10-18T19:00:00Z
---

# ToUnicode CMap × Typography as Linguistic Signal

## The Connection

[[concepts/tounicode-cmap]] is about which character a glyph is. [[concepts/typography-as-linguistic-signal]] is about how the character is set (italic, bold, underline, small caps). The two pages treat these as separate problems. In a PDF they share one source, the font program, and a repair for one can erase the other. ^[inferred]

## Where They Co-occur

- Both pages route through [[entities/junicode]]: the CMap page says a substituted glyph or a MUFI Private Use point extracts as something else; the typography page says that case is "a character-identity problem, not a bold/italic problem".
- Both depend on [[entities/pymupdf]] reading what the file declares, and both end at [[concepts/pdf-text-layer-vs-ocr]].
- Both pages say the font's declared bits cannot be trusted alone. Style flags are often stored wrongly; the CMap may point at the wrong scalar.

## Cross-cutting Insight

The CMap page lists glyph names such as `a.sc` as something repair tools read (pdf-cmap-fixer). The typography page lists small caps as a linguistic signal, often marking a siglum or an expanded abbreviation. A glyph named `a.sc` carries both an identity (`a`) and a style (small caps). A CMap repair that maps it to `a` fixes identity and discards the style. The same repair mapping it to a PUA point keeps the distinction but breaks search. A repair has to emit identity and a style attribute together, or the loss is silent. ^[inferred]

A second consequence is ordering. The CMap page says repairs must run before line joining. Style flags are read from spans, whose font names carry the subset prefix (`ABCDEF+Junicode`). Stripping the prefix to match a known font is common to both steps, so one font-resolution pass can feed the CMap table and the style lookup. ^[inferred]

## Tensions and Trade-offs

- Search wants plain letters; the edition wants the style. Collapsing small caps to lower case serves one reader.
- Eyeballing the page cannot detect either failure: drawing uses glyph ids, so the page looks right while the extracted text is wrong or flat.

## Strongest Objection

The `a.sc` case is an extrapolation. Neither page shows a PDF where the glyph name is the only carrier of small caps. A typesetting engine usually writes ToUnicode entries itself, so the extracted letter may already be `a` with no repair needed, and the style may be recoverable from the font name instead.

> test: in a Junicode PDF set with small caps, what does ToUnicode give for the small-cap glyph, and does the PyMuPDF span report any style hint?

## Open Questions

- Which scholarly fonts store style as glyph variants rather than separate font files?
- Can a repair tool output a per-span style attribute in the same pass?

## Related

- [[concepts/tounicode-cmap]]
- [[concepts/typography-as-linguistic-signal]]
- [[entities/junicode]]
- [[concepts/scholarly-markdown-limits]]
- [[synthesis/Research: Scholarly PDF to Markdown]]
