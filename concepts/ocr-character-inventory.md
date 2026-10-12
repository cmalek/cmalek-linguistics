---
title: >-
    OCR Character Inventory
category: concepts
tags: [ocr, unicode, linguistics]
summary: >-
    A recognizer only emits characters it was trained to emit. List thorn, diacritics, and IPA first, then pick or train the model.
provenance:
  extracted: 0.75
  inferred: 0.20
  ambiguous: 0.05
base_confidence: 0.76
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:20:00Z
relationships:
  - target: "[[references/ocr-for-the-ipa]]"
    type: derived_from
  - target: "[[references/mufi-character-recommendation]]"
    type: uses
  - target: "[[entities/tesseract]]"
    type: related_to
  - target: "[[entities/calamari-ocr]]"
    type: related_to
sources:
  - "url:https://aclanthology.org/2026.eacl-short.19.pdf"
  - "url:https://mufi.info/projects/mufi/pdfs/MUFI%20v4.0%20chart.pdf"
  - "url:https://arxiv.org/pdf/2604.12978"
  - "url:https://sigurdurhaukur.com/articles/ocr-lit-review"
---

# OCR Character Inventory

The character inventory is the set of scalars the output is allowed to contain, including combining marks. A model whose output layer has no slot for a mark will drop it or replace it with a near neighbour. Adding the font to the document does not add the character to the model.

## Key ideas

- [[references/ocr-for-the-ipa]] is the direct measurement for linguistic print. Off-the-shelf Tesseract, Calamari, and Qwen2.5-VL sit around 28–57% CER on IPA lines. After fine-tuning on synthetic IPA in five SIL/Brill fonts, Calamari reaches about 1.4% CER on Japhug lines and 6.8% on an unseen grammar. The failure mode before fine-tuning is substitution of the closest known character.
- [[references/glotocr-bench]] finds the same behaviour across scripts: unfamiliar writing is emitted as a familiar script. Thorn and macron are inside Latin, so a model can score well on “Latin” and still map þ to p. [[references/state-of-icelandic-ocr]] documents that pair, and ð/d, in both older OCR and in vision-language models.
- Build the inventory from the book, not from a language code. For a typical Old English teaching edition, start from [[concepts/old-english-pronunciation]] and [[references/mufi-character-recommendation]]: þ ð æ ǣ ƿ ȝ, vowels with macron, dotted ċ ġ (`U+010A`/`U+010B`, `U+0120`/`U+0121`, or base plus `U+0307`), and whatever IPA the phonology chapter uses. Old Norse adds ǫ and acute vowels. Latin editions add macrons, breves, and sometimes quantity plus accent on one vowel. Old French print adds œ and, in older type, long s `ſ` (`U+017F`).
- Prefer a stated normalization. Precomposed characters where Unicode has them (`ǣ`, `ċ`) survive search and diff better than a surprise mix of composed and decomposed forms. Stacks with no precomposed character stay as base plus combining marks in a fixed order. [[references/olmocr]] scores after NFC, so it will not catch a composed/decomposed split. It will also not catch a missing macron.
- Tesseract will not emit a character absent from the `unicharset`. Fine-tuning has to keep that set large enough. See [[entities/tesseract]]. Kraken and Calamari have the same constraint under different names: the codec of the checkpoint. See [[entities/kraken]] and [[entities/calamari-ocr]].
- A vision-language model has a tokenizer instead of a small codec. Rare scalars may be several tokens, or absent. [[references/ocr-for-the-ipa]] expands Qwen’s tokenizer with the IPA characters before fine-tuning. Without that, generation drifts to neighbours. [[references/reading-or-guessing-vlm-ocr]] shows it will also “repair” a rare sequence into a likely word.
- Synthetic line images in the real fonts (Junicode, Brill, Charis SIL, and the typeface of the book) are the cheap way to grow ground truth. Springmann and colleagues, on Fraktur and early modern Latin (JLCL 2018, GT4HistOCR), found that synthetic Fraktur fonts omit long s and the ligatures real type uses, so real line transcriptions still have to be in the mix.
- eScriptorium’s virtual keyboard is how you put this inventory into a Kraken training set without hunting through a character map. Transkribus’s EVMsaurus minimus (2026) is a handwriting model for English vernacular minuscule, trained to read thorn, eth, wynn, Tironian marks, and abbreviations, with 4.96% CER on its own validation. That number is a manuscript hand, not a textbook face.
- Fine-tuning a Kraken recognizer onto new letters uses `--load` plus a codec mode. `union` adds characters from the new ground truth and keeps the old output layer. `new` drops characters the new set never shows. For þ, macrons, and IPA, `union` is the mode that adds them without deleting the Latin letters the base model already knew. `new` is right only when the new set is the closed inventory of the book and later pages will not introduce another mark. ^[inferred]
- The ground-truth lines have to contain the rare marks often enough. A base model fine-tuned on pages that happen to lack ċ will not grow a ċ. Oversample lines that contain the rare scalars, the way the IPA study did. [[references/ocr-for-the-ipa]].

## Related

- [[concepts/diplomatic-ocr-target]]
- [[concepts/pdf-text-layer-vs-ocr]] — if the text layer is already right, you never ask a model for this inventory
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- [[references/ocr-for-the-ipa]]
- [[references/mufi-character-recommendation]]
- [[references/glotocr-bench]]
- [[references/state-of-icelandic-ocr]]
- [[references/reading-or-guessing-vlm-ocr]]
