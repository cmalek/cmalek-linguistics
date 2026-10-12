---
title: >-
    Diplomatic OCR Target
category: concepts
tags: [ocr, transcription, evaluation]
summary: >-
    Write the transcription rules before correcting. CATMuS is graphemic and drops font style; a linguistic edition must add macrons, dots, and a style channel.
provenance:
  extracted: 0.78
  inferred: 0.16
  ambiguous: 0.06
base_confidence: 0.76
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:45:00Z
relationships:
  - target: "[[concepts/ocr-character-inventory]]"
    type: uses
  - target: "[[references/catmus-guidelines]]"
    type: related_to
  - target: "[[concepts/ocr-evaluation-metrics]]"
    type: related_to
  - target: "[[references/historical-ocr-error-patterns]]"
    type: derived_from
  - target: "[[references/reading-or-guessing-vlm-ocr]]"
    type: derived_from
sources:
  - "url:https://arxiv.org/pdf/2602.14524"
  - "url:https://arxiv.org/html/2605.27750v2"
  - "url:https://huggingface.co/blog/emanuelaboros/can-llms-correct-historical-ocr-without-rewriting"
  - "url:https://sigurdurhaukur.com/articles/ocr-lit-review"
---

# Diplomatic OCR Target

A diplomatic target is the string on the page: the letters, diacritics, and spellings the type actually shows. Normalization of spelling, expansion of abbreviations, and “correction” toward a dictionary are a later editorial policy. They are not part of recognition.

## Key ideas

- [[references/historical-ocr-error-patterns]] states the policy used for eighteenth-century English: keep long s, ligatures, diacritics, punctuation, and capitalization. The only shared cleanup is whitespace and dash-code folding, applied to both the reference and the hypothesis so CER measures graphemes.
- Vision-language models lower CER on that material and also rewrite historical spellings into familiar ones. TrOCR keeps the spelling more often and makes messier local errors. The messier error is the one a corrector can see.
- [[references/reading-or-guessing-vlm-ocr]] shows the same bias under a controlled test. When the image is changed so the letters are implausible, vision-language models move toward a likely word. In-domain [[entities/kraken]] stays closer to the ink. Diacritics are 37–57% of the Greek vision-model errors.
- Post-correction with a generative model has the same failure. Boros lists an “unfaithful” edit as one that keeps the meaning and changes the historical form. [[references/state-of-icelandic-ocr]] notes that CEMI runs OCR correction and spelling normalization as separate stages, and that þ/p confusions often yield another real Icelandic word, so a modern spellchecker accepts them.
- PoCoTo (Vobl et al. 2014, IMPACT / CLARIN-D) is the older interactive tool built for this: a historical lexicon and spelling patterns propose error series, and a person accepts a series in one step. It is aimed at the printed spelling, not at modern English.
- Classroom Old English macrons and dotted `ċ`/`ġ` are editorial, and they are still part of the target when the PDF prints them. [[concepts/old-english-pronunciation]] treats them as teaching marks absent from the manuscripts. [[projects/wyrdcraeft/concepts/diacritic-workflows]] can restore some of them later from a lexicon. Restoration is a different program from copying an edition that already has the marks. ^[inferred]
- Report CER on a gold sample that is dense in the rare characters. An overall CER on ordinary prose hides a systematic macron drop. [[references/olmocr]] normalizes NFC and hyphen variants before scoring; copy that idea only for differences you have decided do not matter, and say so.

## Two policies, written down

[[references/catmus-guidelines]] is the shared graphemic policy for medieval Latin script: keep abbreviation signs, do not expand them, fold letter shapes to modern Latin, fold medieval u/v and i/j, split ligatures, and do not transcribe italic or bold. Medieval tildes and macrons may share one combining mark so that transcribers do not invent distinctions.

A printed linguistic edition needs a stricter file. Keep þ ð æ ƿ, printed macrons, dotted ċ/ġ, and IPA as separate scalars. Do not fold a teaching macron into a tilde. Do not modernize spelling. Record italic, bold, and underline beside the string if they carry meaning, because CATMuS tells you to drop them and a line model will not invent them. [[concepts/typography-as-linguistic-signal]].

Use one policy for ground truth and for [[concepts/ocr-evaluation-metrics]]. Reul’s group mapped macrons to tildes and then scored CER after that mapping, so their 1.5% figure does not mean macrons survived.

## Related

- [[skills/linguistic-pdf-to-markdown]]
- [[concepts/scholarly-markdown-limits]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- [[references/historical-ocr-error-patterns]]
- [[references/reading-or-guessing-vlm-ocr]]
- [[references/state-of-icelandic-ocr]]
- [Can LLMs Correct Historical OCR Without Rewriting History?](https://huggingface.co/blog/emanuelaboros/can-llms-correct-historical-ocr-without-rewriting)
- [PoCoTo](https://github.com/cisocrgroup/PoCoTo)
