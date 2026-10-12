---
title: >-
    OCR Human Correction
category: concepts
tags: [ocr, transcription, workflow]
summary: >-
    Correct a few pages to the diplomatic policy, fine-tune, and correct only what the new model still gets wrong. The model learns your mistakes.
provenance:
  extracted: 0.76
  inferred: 0.18
  ambiguous: 0.06
base_confidence: 0.76
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T18:45:00Z
updated: 2026-10-09T18:45:00Z
relationships:
  - target: "[[concepts/diplomatic-ocr-target]]"
    type: uses
  - target: "[[entities/escriptorium]]"
    type: implements
  - target: "[[concepts/ocr-evaluation-metrics]]"
    type: related_to
sources:
  - "url:https://ub-mannheim.github.io/eScriptorium_Dokumentation/Training-with-eScriptorium-EN.html"
  - "url:https://cistern.cis.lmu.de/ocrocis/tutorial.pdf"
  - "url:https://arxiv.org/pdf/1608.02153"
---

# OCR Human Correction

Correction is ground truth, not a cleanup pass you throw away. The next model copies whatever you leave in the line, including a wrong thorn and a modernized spelling.

## Write the policy first

One page of rules, applied by every corrector, before the first line is fixed. [[concepts/diplomatic-ocr-target]] and [[references/catmus-guidelines]]. If two people encode the same macron differently, CER and the model both treat that as noise. Reul’s comma-versus-virgula “errors” were divergent guidelines in the ground truth, not recognition failures.

## The efficient loop

Mannheim’s eScriptorium guide, for a base model that already “somewhat” reads the page:

1. Run recognition.
2. Correct 2–3 pages completely, including line polygons.
3. Fine-tune that same model on the corrected pages.
4. Run the new model on the next pages.
5. Correct only the remaining errors. Add those pages and fine-tune again.

Ocrocis (Springmann’s OCRopus tutorial) is the same loop with counts: start near 10 pages and at least 300 lines, hold out 10% for testing, train, OCR the next 300 lines with the best checkpoint, correct those, move 10% of the new lines into the test pool. Stop when test error fluctuates with no trend.

Springmann and Lüdeling (2016) found that 100–200 lines of real diplomatic ground truth for one book gave character accuracy above 95%, and that training on the model’s own uncorrected output was worse than that small real set. Pseudo-ground truth saves typing and teaches the errors.

Transkribus asks you to mark a page Ground Truth only after it is fully corrected, then split about 90% train and 10% validation. Their public rule of thumb is CER under 5% as a good result for harder material, and under 1% for simple modern print. Those thresholds are not a diplomatic guarantee. Check the confusion list. ^[inferred]

## What makes correction faster

- Fix segmentation before text. A line that merges a footnote into the body will be transcribed wrong, and the model will learn the merge.
- Use a virtual keyboard that contains only the inventory ([[entities/escriptorium]]). Hunting for þ in a system character map is how diacritics get dropped.
- Correct series, not one token at a time, once the model is stable. PoCoTo groups the same error pattern across a book and lets you accept the group. It was built for historical spelling, so it can tell a real old form from an OCR slip if it has a historical wordlist. [[concepts/diplomatic-ocr-target]].
- Do not “improve” the spelling while you correct. Expansion of abbreviations and u/v normalization are a later file if you want them. CATMuS forbids expansion at transcription time for this reason.
- Keep coordinates. ALTO or PAGE lets you jump from a bad character to the glyph. A bare markdown file does not.

## Style

Line transcription is a string. Bold, italic, and underline are not in that string unless you put markup characters into the ground truth, which makes them part of the CER. [[references/catmus-guidelines]] tell transcribers not to record italic or bold at all. A linguistic edition that needs those styles should keep them as line or span attributes beside the diplomatic string, not by asking the character model to emit asterisks. ^[inferred] See [[concepts/typography-as-linguistic-signal]].

## Related

- [[concepts/ocr-pipeline]]
- [[entities/kraken]]
- [[synthesis/Research: Scholarly PDF to Markdown]]

## Sources

- [Mannheim eScriptorium training](https://ub-mannheim.github.io/eScriptorium_Dokumentation/Training-with-eScriptorium-EN.html)
- [Ocrocis tutorial](https://cistern.cis.lmu.de/ocrocis/tutorial.pdf)
- [[references/ocr-of-historical-printings]]
- [How to train a model in Transkribus](https://www.transkribus.org/blog/how-to-train-a-text-recognition-model-in-transkribus)
- [PoCoTo](https://github.com/cisocrgroup/PoCoTo)
