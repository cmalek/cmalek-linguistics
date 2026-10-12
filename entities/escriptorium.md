---
title: >-
    eScriptorium
category: entities
tags: [ocr, htr, tools, transcription]
summary: >-
    Web app on Kraken for segmenting pages, correcting lines, and fine-tuning a recognizer on those corrections.
provenance:
  extracted: 0.82
  inferred: 0.14
  ambiguous: 0.04
base_confidence: 0.70
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:45:00Z
updated: 2026-10-09T18:45:00Z
relationships:
  - target: "[[entities/kraken]]"
    type: uses
  - target: "[[concepts/ocr-human-correction]]"
    type: implements
sources:
  - "url:https://escriptorium.readthedocs.io/en/latest/train/"
  - "url:https://escriptorium.eu/about/"
---

# eScriptorium

[eScriptorium](https://escriptorium.eu/about/) is the browser interface for [[entities/kraken]]. It imports images or PDFs, segments regions and baselines, runs a recognition model, and stores the correction as ground truth. Training a recognizer is: select parts, Train → Recognizer, pick the transcription version, and optionally pick an existing model to fine-tune. Kraken’s default hyperparameters are used. A fine-tune inherits the base model’s training settings.

Accuracy shown in the UI is character accuracy. CER is the error count divided by the characters to recognize. Each epoch can be downloaded; keep the best validation epoch.

Mannheim’s guide is the practical loop: if a public model already roughly reads the book, correct 2–3 pages, fine-tune, re-run, and add pages only while validation improves. [Training with eScriptorium](https://ub-mannheim.github.io/eScriptorium_Dokumentation/Training-with-eScriptorium-EN.html). From-scratch training of a robust model is described as hundreds of thousands of lines and is better done with the Kraken command line.

The virtual keyboard is where the [[concepts/ocr-character-inventory]] is typed, so þ, combining marks, and abbreviation signs are one key rather than a search through Unicode.

Export is ALTO or PAGE, which is the input to TEI. [[concepts/scholarly-markdown-limits]].

## Related

- [[concepts/ocr-pipeline]]
- [[concepts/ocr-human-correction]]
- [[references/catmus-guidelines]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- <https://escriptorium.eu/about/>
- <https://escriptorium.readthedocs.io/en/latest/train/>
- <https://ub-mannheim.github.io/eScriptorium_Dokumentation/Training-with-eScriptorium-EN.html>
