---
title: >-
    TEI P5 Guidelines
category: entities
tags: [tei, philology, standards, digital-editions]
relationships:
  - target: "[[references/translation-tools-and-scholarly-editing-standards]]"
    type: derived_from
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-academic-output-plan]]"
    type: related_to
sources:
  - "https://tei-c.org/release/doc/tei-p5-doc/en/html/AI.html"
  - "https://tei-c.org/release/doc/tei-p5-doc/en/html/SA.html"
  - "https://tei-c.org/release/doc/tei-p5-doc/en/html/VE.html"
  - "https://tei-c.org/release/doc/tei-p5-doc/en/html/TC.html"
summary: >-
    The Text Encoding Initiative XML standard: word-level lemma and grammar attributes, verse lines, parallel-translation alignment, apparatus and standOff markup, relevant to a reusable export of an annotated translation.
provenance:
  extracted: 0.80
  inferred: 0.15
  ambiguous: 0.05
base_confidence: 0.60
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: peripheral
created: 2026-10-18T22:40:00Z
updated: 2026-10-18T22:40:00Z
---

# TEI P5 Guidelines

The Text Encoding Initiative's XML guidelines for scholarly text. Chapters read in part on 2026-10-18.

- `<w>` is a grammatical word with `lemma`, `lemmaRef` (a pointer to a definition "in an online lexicon"), `pos` and `msd`. The Guidelines say word attributes cannot carry competing tokenisations or tagsets and point to standOff markup.
- Parallel translation: `<ab>` blocks with `xml:id`, linked by `corresp` or `<linkGrp>`; `corresp` on both sides "avoids giving the impression that the English is translating the French".
- Verse: `<lg>` and `<l n="...">`. Critical apparatus: `<app>`, `<lem>`, `<rdg>` with three linking methods.

The app already imports `.tei` and `.xml`; no TEI export exists. See [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-academic-output-plan]].

## Related

- [[references/translation-tools-and-scholarly-editing-standards]]
- [[entities/ycoe]]

## Sources

- [[references/translation-tools-and-scholarly-editing-standards]]
