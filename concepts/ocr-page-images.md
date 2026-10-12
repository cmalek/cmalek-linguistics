---
title: >-
    OCR Page Images
category: concepts
tags: [ocr, imaging, preprocessing]
summary: >-
    Keep an untouched page master, then make one OCR derivative whose crop, deskew, and color match the model you will train.
provenance:
  extracted: 0.72
  inferred: 0.22
  ambiguous: 0.06
base_confidence: 0.74
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:45:00Z
updated: 2026-10-09T18:45:00Z
relationships:
  - target: "[[references/fadgi-digitization-guidelines]]"
    type: derived_from
  - target: "[[concepts/ocr-pipeline]]"
    type: related_to
  - target: "[[entities/kraken]]"
    type: related_to
sources:
  - "url:https://www.digitizationguidelines.gov/guidelines/HIGHLIGHTED_Technical%20Guidelines%20for%20Digitizing%20Cultural%20Heritage%20Materials_3rd%20Edition_05092023.pdf"
  - "url:https://www.loc.gov/ndnp/guidelines/archive/NDNP_201113TechNotes_rev2final.pdf"
  - "url:https://kraken.re/5.3.0/advanced.html"
---

# OCR Page Images

The recognizer never sees the PDF text layer. It sees a raster of the page. That raster is a derivative. The archival master is a different file, and the two should not be the same processing.

## Capture

- [[references/fadgi-digitization-guidelines]] (3rd edition, 2023): master files are not retouched. Image the whole page plus a small margin past the edge. Special-collections notes allow capture above 400 ppi and do not require it for 4-star compliance. Document tables in that guideline use a 400 ppi class (down to 396 ppi) and a 300 ppi class (down to 294 ppi). One-star imaging is called out as not useful for OCR.
- NDNP newspaper practice: 8-bit grayscale TIFF, about 300–400 dpi, one page per file. Deskew when skew exceeds 3 degrees. Crop to the page edge plus up to 1/4 inch, not to the text block, so marginal notes survive. Do the crop and deskew on the TIFF before OCR, because word coordinates have to match that image. The master delivered to LC matches that crop and deskew and does not include binarization, sharpening, or contrast tricks used only to help OCR.
- A PDF that is already a scan: render each page to a lossless image (TIFF or PNG) at the pixel size of the scan. Do not downsample to a screen preview. Do not read the text layer while rendering.
- Camera photos add perspective and uneven light. FADGI prefers a single-exposure capture of the whole page. Glass or vacuum flattening of a fragile original needs a conservator. Those are capture rules, not OCR tricks.

## The OCR derivative

Freeze one recipe and use it for ground truth and for later pages. A model trained on one preprocessing fails on another. ^[inferred]

- [[entities/kraken]]’s baseline segmenter runs on grayscale or color. Its docs say binarization is deprecated and often hurts uneven lighting or faint ink. The old bounding-box segmenter still requires a binary image.
- [[references/mixed-model-historical-ocr]] trained Calamari mostly on binarized lines, and also tried grayscale. Their best book-specific finetune was sensitive to which binarization was used. Staatsbibliothek binarization beat the default in that study. The lesson is consistency with the checkpoint, not “always binarize.”
- Deskew and page-edge crop belong in the derivative when lines are badly rotated. Aggressive stain removal, hole fill, and contrast stretches change glyphs. Keep them off the master. If you use them on the derivative, the ground-truth lines must be cut from that same derivative.
- Split two-up scans into one page per file before segmentation. NDNP requires this. A model that sees two pages as one page will invent a reading order. ^[inferred]

## Related

- [[concepts/ocr-pipeline]]
- [[concepts/pdf-text-layer-vs-ocr]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- [[references/fadgi-digitization-guidelines]]
- [NDNP 2011 technical guidelines](https://www.loc.gov/ndnp/guidelines/archive/NDNP_201113TechNotes_rev2final.pdf)
- [Kraken advanced usage](https://kraken.re/5.3.0/advanced.html)
- [[references/mixed-model-historical-ocr]]
