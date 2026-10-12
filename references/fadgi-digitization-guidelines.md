---
title: >-
    FADGI Still Image Guidelines
category: references
tags: [imaging, archives, ocr]
sources:
  - "url:https://www.digitizationguidelines.gov/guidelines/HIGHLIGHTED_Technical%20Guidelines%20for%20Digitizing%20Cultural%20Heritage%20Materials_3rd%20Edition_05092023.pdf"
source_url: "https://www.digitizationguidelines.gov/guidelines/HIGHLIGHTED_Technical%20Guidelines%20for%20Digitizing%20Cultural%20Heritage%20Materials_3rd%20Edition_05092023.pdf"
summary: >-
    US federal still-image guideline. Masters stay unretouched; OCR uses a derivative. Star tiers set resolution, and 1-star is not for OCR.
provenance:
  extracted: 0.84
  inferred: 0.12
  ambiguous: 0.04
base_confidence: 0.62
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:45:00Z
updated: 2026-10-09T18:45:00Z
relationships:
  - target: "[[concepts/ocr-page-images]]"
    type: related_to
---

# FADGI Still Image Guidelines

Federal Agencies Digital Guidelines Initiative, *Technical Guidelines for Digitizing Cultural Heritage Materials*, 3rd edition, 9 May 2023. [PDF](https://www.digitizationguidelines.gov/guidelines/HIGHLIGHTED_Technical%20Guidelines%20for%20Digitizing%20Cultural%20Heritage%20Materials_3rd%20Edition_05092023.pdf).

## Key claims

- Derivative files, including files made for OCR, HCR, or HTR, are produced from a master. They are not the archival object. Lossy access JPEGs are a typical derivative and are a poor OCR input. ^[inferred]
- One-star imaging is informational only and “will not be useful for optical character recognition.” Two-star “may or may not be suitable for OCR.” Three- and four-star are the levels aimed at reuse.
- Resolution tables use a 300 ppi class (tolerance to 294 ppi) and a 400 ppi class (tolerance to 396 ppi). For special collections, capture above 400 ppi is allowed and is not required to reach 4-star.
- Masters: no retouching. Include the whole page and a small amount beyond the edge. Do not hold a fragile original under glass, or on a vacuum board, without a conservator. Single-exposure capture of the whole page is the preferred technology.
- NDNP’s newspaper profile is the practical OCR companion, not a FADGI star table: grayscale TIFF, 300–400 dpi, deskew above 3 degrees, crop to the page edge plus up to 1/4 inch, and keep binarization and sharpening off the master that coordinates are measured against. [NDNP 2011 technical notes](https://www.loc.gov/ndnp/guidelines/archive/NDNP_201113TechNotes_rev2final.pdf).

## Limitations

FADGI specifies images, not a recognizer and not a diplomatic transcription policy. A 400 ppi master can still fail OCR if the derivative’s binarization does not match the model. See [[entities/kraken]].

## Related

- [[concepts/ocr-page-images]]
- [[concepts/ocr-pipeline]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- <https://www.digitizationguidelines.gov/guidelines/HIGHLIGHTED_Technical%20Guidelines%20for%20Digitizing%20Cultural%20Heritage%20Materials_3rd%20Edition_05092023.pdf>
- <https://www.loc.gov/ndnp/guidelines/archive/NDNP_201113TechNotes_rev2final.pdf>
