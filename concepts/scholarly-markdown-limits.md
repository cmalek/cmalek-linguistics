---
title: >-
    Scholarly Markdown Limits
category: concepts
tags: [markdown, layout, tei, ocr]
summary: >-
    Markdown keeps bold, italic, and simple tables. Underline, small caps, font, and merged paradigm cells need HTML or TEI beside the markdown.
provenance:
  extracted: 0.74
  inferred: 0.22
  ambiguous: 0.04
base_confidence: 0.75
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:20:00Z
relationships:
  - target: "[[concepts/typography-as-linguistic-signal]]"
    type: uses
  - target: "[[entities/docling]]"
    type: uses
  - target: "[[concepts/pdf-text-layer-vs-ocr]]"
    type: related_to
sources:
  - "url:https://docling-project.github.io/docling/concepts/serialization/"
  - "url:https://github.com/docling-project/docling-core/blob/main/docling_core/transforms/serializer/markdown.py"
  - "url:https://tei-c.org/release/doc/tei-p5-doc/en/html/TC.html"
---

# Scholarly Markdown Limits

Markdown is a good delivery format for a reading text. It is a poor archive of a scholarly page. Produce markdown from a richer intermediate (HTML, ALTO, PAGE, or TEI), and keep that intermediate.

## What markdown can hold

- `**bold**` and `*italic*` round-trip in CommonMark. [[entities/docling]]’s markdown serializer writes exactly those, plus `~~strikethrough~~`.
- Pipe tables hold a grid of cells when every cell is a rectangle and the header is one row.
- Footnote syntax (`[^1]`) can hold a note whose anchor is a superscript number, after you have decided the note is a note and not a critical apparatus.
- Unicode itself is fine. A macron, thorn, or IPA letter needs no markdown extension once the scalar is correct.

## What markdown flattens

- Docling’s HTML serializer emits underline as `<u>`, and table cells as `rowspan` / `colspan`. The markdown table serializer writes the spanned text only in the origin cell and leaves the covered cells empty. The project’s serialization guide says to use HTML or the document dict when merged headers matter. Paradigm tables in grammars are full of those merges. ^[inferred]
- There is no CommonMark for small caps, font family, point size, color, or letter-spacing. Those are the cues that separate a headword, a cited form, a siglum, and a gloss. Keep them as raw HTML (`<span class="small-caps">`, `<u>`) inside the markdown, or keep the HTML as the master and generate markdown from it.
- A critical apparatus is structured variant data (`<app>`, `<lem>`, `<rdg>` in the [TEI critical apparatus chapter](https://tei-c.org/release/doc/tei-p5-doc/en/html/TC.html)). A bottom-of-page note in the PDF is only the print rendering. ekdosis and ConTeXt typeset that structure; they are the reverse direction (TEI to PDF). Going from the printed apparatus back to TEI is a segmentation and linking problem, not a markdown export.
- Multi-column reading order, marginal glosses, and line-end hyphens have to be decided before the markdown is written. Gabay and Clérice’s early-French pipeline converts Kraken and YALTAi ALTO into TEI: main text in reading order, running titles and quire marks in `<fw>`, and a removed end-of-line hyphen still marked with `<lb/>` ([CEUR Vol-3834, paper 21](https://ceur-ws.org/Vol-3834/paper21.pdf)). They then run a separate spelling-normalization pass back into the TEI. Keep that pass optional if the goal is a diplomatic copy.
- ALTO and PAGE XML are the usual OCR intermediates because they store coordinates. Scheithauer, Chagué, and Romary argue for mapping that output into one TEI file early, with the recognition layer and the editorial layer both present ([hal-04001303](https://inria.hal.science/hal-04001303)). Markdown can be generated from the edition view. It should not be the only stored form.
- Converters that “remove headers and footers” ([[entities/marker-pdf]], and olmOCR-Bench tests that reward absence) will drop folio numbers and running titles. For a linguistic book those are often wanted in a sidecar, even when they are unwanted in the chapter text.

## Related

- [[concepts/typography-as-linguistic-signal]]
- [[entities/docling]]
- [[entities/kraken]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- [Docling serialization](https://docling-project.github.io/docling/concepts/serialization/)
- [Docling markdown serializer](https://github.com/docling-project/docling-core/blob/main/docling_core/transforms/serializer/markdown.py)
- [TEI critical apparatus](https://tei-c.org/release/doc/tei-p5-doc/en/html/TC.html)
- [[references/olmocr]]
