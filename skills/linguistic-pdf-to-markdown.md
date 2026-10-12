---
title: >-
    Linguistic PDF to Markdown
category: skills
tags: [ocr, pdf, workflow, linguistics]
summary: >-
    Render every page, ignore the text layer, then segment, recognize, correct, and fine-tune until held-out CER and the rare-character list pass.
provenance:
  extracted: 0.58
  inferred: 0.36
  ambiguous: 0.06
base_confidence: 0.76
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:20:00Z
updated: 2026-10-09T18:45:00Z
relationships:
  - target: "[[concepts/ocr-pipeline]]"
    type: implements
  - target: "[[concepts/ocr-page-images]]"
    type: uses
  - target: "[[concepts/diplomatic-ocr-target]]"
    type: uses
  - target: "[[concepts/ocr-human-correction]]"
    type: uses
sources:
  - "url:https://arxiv.org/pdf/1608.02153"
  - "url:https://arxiv.org/pdf/2106.07881"
  - "url:https://catmus-guidelines.github.io/"
  - "url:https://www.digitizationguidelines.gov/guidelines/HIGHLIGHTED_Technical%20Guidelines%20for%20Digitizing%20Cultural%20Heritage%20Materials_3rd%20Edition_05092023.pdf"
---

# Linguistic PDF to Markdown

Image-only recognition for linguistic and dead-language PDFs whose text layer is missing or corrupt. Markdown is still the last export. The file you correct is ALTO, PAGE, or TEI, with the diplomatic string and a separate place for bold, italic, and underline. Research write-up: [[synthesis/Research: Scholarly PDF to Markdown]].

Do not let [[entities/marker-pdf]], [[entities/docling]], or [[references/olmocr]] read the text layer. A corrupt layer copied into the markdown is the failure this workflow exists to avoid. [[concepts/pdf-text-layer-vs-ocr]].

## 1. Write the diplomatic policy

One page, before any correction. [[concepts/diplomatic-ocr-target]].

- Keep the printed letters: þ ð æ ƿ ȝ, macrons, breves, dots, accents, IPA, long s if it is printed.
- Do not expand abbreviations. Do not modernize spelling.
- [[references/catmus-guidelines]] is the manuscript baseline (graphemic, no italic/bold, medieval u/v folded). A textbook edition adds the marks and the style channel CATMuS drops.
- The same rules apply to ground truth and to scoring.

## 2. Make page images

[[concepts/ocr-page-images]].

- From a scanned PDF, render one lossless page image per page at the scan’s pixel size.
- From a camera or a new capture, follow [[references/fadgi-digitization-guidelines]]: full page plus margin, no retouching of the master. OCR gets a derivative.
- Deskew only when the page is visibly rotated (NDNP uses 3 degrees). Crop to the page edge, not the text block, so notes in the margin remain.
- Freeze color treatment. [[entities/kraken]] baseline models want grayscale or color. A Calamari checkpoint trained on binarized lines wants that same binarization. Do not mix them.

## 3. Segment, then recognize

[[concepts/ocr-pipeline]]. In [[entities/escriptorium]]:

1. Import the images.
2. Run a baseline segmenter. Correct regions and lines on a sample before you trust the text. Label body, table, footnote, apparatus, and marginalia if the page has them.
3. Run the closest public recognizer (Latin print, or a medieval Latin print model). Expect þ, macrons, and IPA to be wrong. That first pass is only there to save typing.
4. Export ALTO or PAGE when you leave the tool. Generate markdown from that, not from the tool’s plain text.

## 4. Correct a little, then fine-tune

[[concepts/ocr-human-correction]].

1. Correct line polygons and the diplomatic string on 2–3 pages if the base model already roughly reads the type. Otherwise aim for about 100–200 lines of real transcription for one book ([[references/ocr-of-historical-printings]]), or about 300 lines / 10 pages to start the Ocrocis loop.
2. Hold out 10% of lines, ideally whole pages the model will not train on.
3. Fine-tune. In Kraken, load the base model and use codec mode `union` so new letters are added and the old alphabet stays. [[concepts/ocr-character-inventory]]. Put the rare marks on a virtual keyboard and make sure the training lines actually contain them.
4. Re-run on the next pages. Correct what remains. Add those pages. Stop when held-out error stops falling.
5. Do not train on uncorrected model output. The model learns it.
6. The model copies your mistakes. One policy, one corrector’s habits, or the confusion list fills up with guideline splits.

From-scratch training of a general model is a different project (thousands of lines). Finetuning a polyfont model is the cheap one: [[references/mixed-model-historical-ocr]] cut CER roughly in half versus training from scratch, in a few CPU hours, on historical Latin print. Their ground truth had already folded macrons into tildes, so repeat the measurement on your policy.

## 5. Measure before a batch

[[concepts/ocr-evaluation-metrics]].

- Held-out CER, plus counts for þ/p, ð/d, dropped macrons, dropped dots, long s/f, and whitespace merges.
- One paradigm table, cell by cell, including merged headers. Markdown will flatten those; keep the HTML or TEI table. [[concepts/scholarly-markdown-limits]].
- One note and one apparatus entry still attached to the right place.
- A fluent page audited for missing diacritics.

Style (italic, bold, underline) is checked on the attribute layer, not inside CER, unless you deliberately put markup characters in the string.

## 6. Only then export markdown

HTML or TEI remains the master. Markdown gets `**bold**` and `*italic*` where you mapped the style attributes, raw `<u>` for underline, and HTML tables where cells span. Running titles and page numbers stay in a sidecar. A later lexicon pass such as [[projects/wyrdcraeft/concepts/diacritic-workflows]] can add macrons to a text that never had them. It should not have to restore marks the edition already printed and the OCR dropped.

## Related

- [[concepts/ocr-page-images]]
- [[concepts/ocr-pipeline]]
- [[concepts/ocr-human-correction]]
- [[concepts/ocr-evaluation-metrics]]
- [[entities/kraken]]
- [[entities/calamari-ocr]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- [[references/fadgi-digitization-guidelines]]
- [[references/catmus-guidelines]]
- [[references/ocr-of-historical-printings]]
- [[references/mixed-model-historical-ocr]]
- [[references/ocr-for-the-ipa]]
