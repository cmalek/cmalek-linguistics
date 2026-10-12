---
title: >-
    PDF Text Layer versus OCR
category: concepts
tags: [ocr, pdf, workflow]
summary: >-
    A corrupt or empty PDF text layer is ignored. Render the page and recognize the image. A tool that trusts a bad layer will copy the corruption.
provenance:
  extracted: 0.70
  inferred: 0.25
  ambiguous: 0.05
base_confidence: 0.74
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:45:00Z
relationships:
  - target: "[[concepts/tounicode-cmap]]"
    type: related_to
  - target: "[[concepts/ocr-page-images]]"
    type: related_to
  - target: "[[concepts/diplomatic-ocr-target]]"
    type: related_to
  - target: "[[entities/pymupdf]]"
    type: uses
sources:
  - "url:https://pymupdf.readthedocs.io/en/latest/textpage.html"
  - "url:https://arxiv.org/html/2605.27750v2"
  - "url:https://github.com/romain-girardi-eng/regreek"
---

# PDF Text Layer versus OCR

A PDF page is a picture plus, sometimes, a hidden string of character codes. For the linguistic PDFs in this research, that string is either missing or corrupted. The operating rule is to render the page to an image and recognize the image. See [[concepts/ocr-page-images]] and [[skills/linguistic-pdf-to-markdown]].

## Key ideas

- A corrupt text layer is worse than an empty one when a converter trusts it. [[entities/marker-pdf]], [[entities/docling]], and [[references/olmocr]] read the text layer where one exists and OCR only the rest. On these books, turn that shortcut off. Force a full-page render. ^[inferred]
- The picture can still be perfect while the string is Latin, boxes, or Private Use Area. That is a broken [[concepts/tounicode-cmap]]. Repairing the map is possible for some legacy Greek fonts ([[entities/regreek]]). It is not the plan for this corpus.
- Recognition then has to carry the character inventory, the diplomatic policy, and any typography you still need. Line OCR does not recover bold or italic by itself. See [[concepts/typography-as-linguistic-signal]] and [[concepts/ocr-character-inventory]].
- A text layer that really does paste þ, macrons, and italic correctly is a different job, and it keeps font metadata that OCR has to rediscover. That path stays documented here so it is not confused with the image pipeline. It is not the default.

## Related

- [[skills/linguistic-pdf-to-markdown]] — the decision procedure
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- [PyMuPDF text extraction](https://pymupdf.readthedocs.io/en/latest/textpage.html)
- [[references/reading-or-guessing-vlm-ocr]]
- [[references/olmocr]]
- [regreek](https://github.com/romain-girardi-eng/regreek)
