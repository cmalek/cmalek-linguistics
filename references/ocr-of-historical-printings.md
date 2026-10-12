---
title: >-
    OCR of Historical Printings
category: references
tags: [ocr, training, ground-truth]
sources:
  - "url:https://arxiv.org/pdf/1608.02153"
source_url: "https://arxiv.org/pdf/1608.02153"
summary: >-
    Springmann and Lüdeling: book-specific models from 100–200 real lines beat training on the model’s own uncorrected output.
provenance:
  extracted: 0.84
  inferred: 0.12
  ambiguous: 0.04
base_confidence: 0.67
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:45:00Z
updated: 2026-10-09T18:45:00Z
relationships:
  - target: "[[concepts/ocr-human-correction]]"
    type: related_to
  - target: "[[concepts/diplomatic-ocr-target]]"
    type: related_to
---

# OCR of Historical Printings

Uwe Springmann and Anke Lüdeling, on OCR for historical print and the RIDGES herbal corpus. The preprint used here is [arXiv:1608.02153](https://arxiv.org/pdf/1608.02153). The Ocrocis tutorial ([PDF](https://cistern.cis.lmu.de/ocrocis/tutorial.pdf)) is the matching how-to for the OCRopus tooling of that period. A 2015 lecture states a larger “about 200 pages” figure for a general model; the book-specific numbers below are the ones to use for one typeface.

## Key claims

- Line images are transcribed diplomatically. Ground truth is `*.gt.txt` beside a line image. The engine in these experiments does not use a language model, which is why odd spellings can be learned instead of “corrected.”
- Individual models, trained on one book’s type, are best on the unseen pages of that book and poor on other books. Mixed models generalize, at some cost in accuracy on each single book.
- About 100–200 printed lines of real ground truth consistently gave character accuracy above 95% for a book-specific model. Training on the recognizer’s own uncorrected output, as pseudo-ground truth, was worse than that small real set.
- Ocrocis rule of thumb: begin with about 10 good pages and at least 300 lines, hold out 10% for testing, train, then OCR the next batch and correct it. Add data until the test error stops trending down. They cite useful models in the 1,000–5,000 line range when the type mix is wide, which is a different target from one book.
- A 2015 slide for one early printing (Bodenstein) shows error falling to about 1–2% within a few dozen pages, with extra pages mostly reducing variance. The same talk’s “transcribe about 200 pages” line is the cost of a broader model, not the first useful book-specific checkpoint. ^[ambiguous]

## Limitations

These are OCRopus-era print experiments on Latin-script books, not IPA and not Old English textbooks. The diplomatic target here is the printed line, including historical spelling. It is not a full page with font style.

## Related

- [[concepts/ocr-human-correction]]
- [[references/mixed-model-historical-ocr]] — the later polyfont Calamari result
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- <https://arxiv.org/pdf/1608.02153>
- <https://cistern.cis.lmu.de/ocrocis/tutorial.pdf>
