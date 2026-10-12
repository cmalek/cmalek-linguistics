---
title: >-
    Marker
category: entities
tags: [ocr, markdown, layout, tools]
summary: >-
    PDF-to-markdown converter that prefers the text layer and OCRs the rest. Strong on English layout benches; header stripping can drop edition furniture.
provenance:
  extracted: 0.76
  inferred: 0.18
  ambiguous: 0.06
base_confidence: 0.68
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:20:00Z
relationships:
  - target: "[[concepts/pdf-text-layer-vs-ocr]]"
    type: implements
  - target: "[[references/olmocr]]"
    type: related_to
  - target: "[[entities/docling]]"
    type: related_to
sources:
  - "url:https://github.com/datalab-to/marker"
---

# Marker

[Marker](https://github.com/datalab-to/marker) (Datalab) converts PDF, images, and office files to markdown, JSON, HTML, and chunks. It reads a text layer when one exists and OCRs image regions. Weights are Apache-2.0 code with a separate model license. An optional `--use_llm` pass (Gemini, Claude, OpenAI-compatible, Ollama) merges cross-page tables and formats inline math. The hosted sibling model is Chandra.

## Scores they publish

On olmOCR-Bench, Marker’s README (balanced, GPU) reports 76.0 overall and 83.5 on born-digital pages, about 2.9 pages/second. Fast mode is 66.6 / 71.6 at 7.4 pages/second. Fast with OCR off is 43.6 / 55.8. Their table lists MinerU’s pipeline at 72.7 and Docling at 50.3. Chandra hosted is 85.8. MinerU also publishes a different number on OmniDocBench (MinerU2.5-Pro at 95.69), which is not this bench.

A July 2026 third-party comparison used Marker 2.0 fast and found it ahead on reading order and scanned text, and behind Docling on table structure. See [[entities/docling]].

## Cautions for linguistic books

- The README lists header and footer removal as a feature. Keep a JSON or HTML dump if folio numbers and running titles matter. See [[concepts/scholarly-markdown-limits]].
- Born-digital quality depends on the text layer. A broken [[concepts/tounicode-cmap]] is copied faithfully into the markdown.
- LLM boost mode can rewrite tables and forms. That is the behaviour [[concepts/diplomatic-ocr-target]] warns about. Use it after the character inventory checks out, or not at all, on a dead-language edition. ^[inferred]
- Nothing in the public bench measures þ, macrons, or IPA.

## Related

- [[references/olmocr]]
- [[skills/linguistic-pdf-to-markdown]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- <https://github.com/datalab-to/marker>
- <https://huggingface.co/opendatalab/MinerU2.5-Pro-2605-1.2B>
