---
title: >-
    Docling
category: entities
tags: [ocr, markdown, layout, tools]
summary: >-
    IBM document parser: layout, TableFormer tables, pluggable OCR, and export to markdown, HTML, or JSON. Markdown drops merged cells.
provenance:
  extracted: 0.78
  inferred: 0.16
  ambiguous: 0.06
base_confidence: 0.72
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:20:00Z
relationships:
  - target: "[[concepts/scholarly-markdown-limits]]"
    type: implements
  - target: "[[concepts/pdf-text-layer-vs-ocr]]"
    type: related_to
sources:
  - "url:https://docling.org/doc/"
  - "url:https://docling-project.github.io/docling/concepts/serialization/"
---

# Docling

[Docling](https://docling.org/doc/) (IBM Research, open source) is a document-understanding pipeline, not a single OCR engine. It detects layout, recovers reading order, runs TableFormer on tables, and calls an OCR engine only where the page has no usable text. OCR plugins include RapidOCR, Tesseract, EasyOCR, OcrMac, and Nemotron. A separate VLM pipeline has presets (Granite Docling, SmolDocling, DeepSeek-OCR, MinerU2.5-Pro, GLM-OCR, Chandra OCR 2, and others).

## Export

The markdown serializer writes `**bold**`, `*italic*`, and `~~strike~~`. The HTML serializer writes underline and real `rowspan`/`colspan`. The [serialization guide](https://docling-project.github.io/docling/concepts/serialization/) says markdown tables put spanned text in the origin cell and leave the other cells blank. For a paradigm table, export HTML or JSON and derive a simpler markdown view from that. See [[concepts/scholarly-markdown-limits]].

## How to read the benchmarks

On the Marker project’s olmOCR-Bench comparison, default Docling scores about 50 overall, behind Marker balanced at 76. A July 2026 third-party run (Docling 2.117, TableFormer accurate) passed 38 of 40 table-structure checks, ahead of Marker 2.0 fast at 31 of 40, and Marker led reading order (44 of 54). The two benches do not name a single winner. Neither bench is a thorn or IPA test. See [[references/olmocr]].

Docling’s default OCR language in that third-party run was English RapidOCR. An English OCR plugin will damage þ and IPA on any region it rasterizes. ^[inferred] Force the text layer when the probe in [[concepts/pdf-text-layer-vs-ocr]] succeeds, or point OCR at a model whose inventory matches the book.

## Related

- [[entities/marker-pdf]]
- [[entities/pymupdf]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- <https://docling.org/doc/>
- <https://docling-project.github.io/docling/concepts/serialization/>
- <https://pdftomdconverter.app/research/best-pdf-to-markdown-converter-benchmark>
