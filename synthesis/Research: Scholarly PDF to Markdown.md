---
title: >-
    Research: Scholarly PDF to Markdown
category: synthesis
tags: [ocr, pdf, unicode, linguistics, research]
sources:
  - "url:https://arxiv.org/pdf/1608.02153"
  - "url:https://arxiv.org/pdf/2106.07881"
  - "url:https://catmus-guidelines.github.io/"
  - "url:https://www.digitizationguidelines.gov/guidelines/HIGHLIGHTED_Technical%20Guidelines%20for%20Digitizing%20Cultural%20Heritage%20Materials_3rd%20Edition_05092023.pdf"
  - "url:https://aclanthology.org/2026.eacl-short.19.pdf"
  - "url:https://arxiv.org/html/2605.27750v2"
  - "url:https://arxiv.org/pdf/2602.14524"
summary: >-
    Image-only OCR for linguistic PDFs with a bad or missing text layer: capture, diplomatic rules, CER, correction, and fine-tuning.
provenance:
  extracted: 0.64
  inferred: 0.28
  ambiguous: 0.08
base_confidence: 0.76
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:45:00Z
relationships:
  - target: "[[skills/linguistic-pdf-to-markdown]]"
    type: related_to
  - target: "[[concepts/ocr-pipeline]]"
    type: related_to
  - target: "[[concepts/diplomatic-ocr-target]]"
    type: related_to
  - target: "[[concepts/ocr-human-correction]]"
    type: related_to
---

# Research: Scholarly PDF to Markdown

These PDFs are recognized from page images. The text layer is missing or corrupted, and a converter that trusts it will copy the corruption. The workable loop is: render a page, segment lines, recognize with a model whose alphabet includes the rare marks, correct a small diplomatic sample, fine-tune, and stop when held-out character error and the rare-character list stop moving.

The procedure is [[skills/linguistic-pdf-to-markdown]]. An earlier pass of this page treated a good text layer as the default. That path is now a side note on [[concepts/pdf-text-layer-vs-ocr]]. It is not the plan for this corpus.

## Overview

Capture or render one lossless image per page, and keep an unretouched master separate from the OCR derivative. Write the transcription rules before anyone corrects a line. Fine-tune a line recognizer (Kraken or Calamari) on those corrections. A few hundred real lines of one book already beat training on the model’s own guesses. General PDF-to-markdown scores do not measure thorn, macrons, or IPA. CATMuS is the shared graphemic standard for medieval Latin script, and it deliberately drops italic, bold, and some macron/tilde distinctions a linguistic edition may need to keep.

## Key findings

- Ignore the text layer. [[entities/marker-pdf]], [[entities/docling]], and [[references/olmocr]] prefer it when it exists. Force a render. [[concepts/pdf-text-layer-vs-ocr]].
- Masters and OCR derivatives are different files. FADGI: no retouching of the master, full page plus margin, 1-star imaging is not for OCR, resolution classes at 300 and 400 ppi. NDNP: deskew past 3 degrees, crop to the page edge plus a quarter inch, and keep binarization off the master that coordinates refer to. [[concepts/ocr-page-images]], [[references/fadgi-digitization-guidelines]].
- Match preprocessing to the checkpoint. Kraken’s baseline segmenter wants grayscale or color; its docs call binarization deprecated. Reul’s Calamari models were trained on specific binarizations, and the binarization changed the CER. [[entities/kraken]], [[references/mixed-model-historical-ocr]].
- Split the pipeline. Segmentation, recognition, and reading order are separate models. A character model cannot repair a line that swallowed a footnote. [[concepts/ocr-pipeline]]. Page-level word error mixes recognition with reading order; report them apart. [[concepts/ocr-evaluation-metrics]].
- Diplomatic policy is part of the model. CATMuS keeps abbreviation signs, forbids expansion, folds medieval letter shapes, and tells you not to transcribe italic or bold. A textbook that uses macrons, dotted consonants, and italic as notation needs extra rules, used both in the ground truth and in the score. [[references/catmus-guidelines]], [[concepts/diplomatic-ocr-target]].
- How much to correct: 2–3 pages to start a fine-tune when a base model already roughly reads the type (Mannheim / eScriptorium). About 100–200 real lines for a book-specific model above 95% character accuracy (Springmann and Lüdeling). About 300 lines, then OCR-and-correct the next batch, in the Ocrocis loop. Training on uncorrected pseudo-ground truth was worse than the small real set. A general from-scratch model is thousands of lines, not a weekend. [[concepts/ocr-human-correction]], [[references/ocr-of-historical-printings]].
- Finetune, do not start from zero, once a close model exists. Reul et al. reached about 1.50% CER by finetuning a polyfont Calamari model, versus 2.98% from scratch, in a few CPU hours. Their guidelines had already mapped macrons to tildes. Kraken `union` adds new letters to a loaded codec; `new` replaces the alphabet. [[entities/calamari-ocr]], [[concepts/ocr-character-inventory]].
- Off-the-shelf models miss the inventory. IPA lines sit around 28–57% CER until fine-tuning; Calamari on synthetic IPA then reaches about 1.4% on one grammar. þ/p and ð/d persist in vision models. Greek vision-model errors are 37–57% diacritics, and those models rewrite implausible spellings. [[references/ocr-for-the-ipa]], [[references/reading-or-guessing-vlm-ocr]], [[references/state-of-icelandic-ocr]], [[references/historical-ocr-error-patterns]].
- Style is a second channel. Line OCR and CATMuS both omit bold and italic. Keep them as attributes if they are linguistic. [[concepts/typography-as-linguistic-signal]]. Markdown cannot hold underline, small caps, or merged table cells; store HTML or TEI. [[concepts/scholarly-markdown-limits]].
- The model copies the corrector. Divergent guidelines showed up as fake comma/virgula errors in GT4HistOCR. Whitespace merges were the largest real error class in the mixed Latin model.

## Core concepts

- [[concepts/ocr-page-images]] — master versus OCR derivative
- [[concepts/ocr-pipeline]] — segment, recognize, order
- [[concepts/ocr-human-correction]] — the correct-and-finetune loop
- [[concepts/ocr-evaluation-metrics]] — CER, confusions, held-out pages
- [[concepts/diplomatic-ocr-target]] — what the string is allowed to change
- [[concepts/ocr-character-inventory]] — the scalars the codec must grow
- [[concepts/typography-as-linguistic-signal]] — style beside the string
- [[concepts/pdf-text-layer-vs-ocr]] — why the text layer stays off
- [[concepts/scholarly-markdown-limits]] — export, not the master

## Entities and tools

- [[entities/escriptorium]] — correct, fine-tune, and export on top of Kraken
- [[entities/kraken]] — baseline segmentation and recognition
- [[entities/calamari-ocr]] — line OCR; strongest published IPA fine-tune and the 2021 polyfont print model
- [[entities/tesseract]] — usable after the unicharset contains the marks; weak out of the box on IPA and Fraktur
- [[entities/junicode]] — the typeface the inventory has to survive
- [[entities/pymupdf]] — can render pages; do not use it to read these text layers

## Contradictions and open questions

- **How many pages to transcribe** depends on the target. Springmann’s 2015 talk says about 200 pages for a broad model and also shows one book nearing 1–2% CER within a few dozen pages. The 2016 paper’s 100–200 lines are book-specific. Mannheim’s 2–3 pages assume a base model that already roughly works. These are three regimes, not one number. ^[ambiguous]
- **Binarize or not.** NDNP-era practice binarizes only the OCR derivative. Kraken now says binarization often hurts. Reul’s best Calamari numbers used a chosen binarization. Follow the checkpoint.
- **CATMuS versus a facsimile edition.** CATMuS folds shapes and drops font style so that many transcribers agree. A grammar’s italic and macrons are meaningful. Using CATMuS unchanged will train a model that cannot emit the edition you want.
- **Reul’s 1.5% CER** is after macron-to-tilde and whitespace rules. It is not a score for this diplomatic policy.
- **No published CER** on a Junicode Old English or Old Norse textbook with macrons, dotted consonants, and paradigm tables. The IPA, Icelandic, and historical-Latin results are the nearest evidence.
- **olmOCR-Bench and OmniDocBench** still do not test this inventory. They are irrelevant to the go/no-go decision here.

## Sources consulted

- [[references/fadgi-digitization-guidelines]]
- [[references/catmus-guidelines]]
- [[references/ocr-of-historical-printings]]
- [[references/mixed-model-historical-ocr]]
- [[references/ocr-for-the-ipa]]
- [[references/reading-or-guessing-vlm-ocr]]
- [[references/historical-ocr-error-patterns]]
- [[references/state-of-icelandic-ocr]]
- [[references/glotocr-bench]]
- [[references/olmocr]]
- [[references/mufi-character-recommendation]]
- [[references/junicode-manual]]
- [Kraken training](https://kraken.re/6.0.0/tutorials/training.html)
- [eScriptorium training](https://escriptorium.readthedocs.io/en/latest/train/)
- [Ocrocis tutorial](https://cistern.cis.lmu.de/ocrocis/tutorial.pdf)
- [End-to-end page-level HTR assessment](https://export.arxiv.org/pdf/2301.05935v2.pdf)

## Sources

- The pages and URLs in Sources consulted are the evidence for this synthesis.
