---
title: >-
  A Morphological Analyzer for Old English Verbs (Adams)
category: references
tags: [old-english, morphology, finite-state]
sources:
  - "url:http://www.cs.cmu.edu/~jmadams/NLPLabProject.pdf"
source_url: "http://www.cs.cmu.edu/~jmadams/NLPLabProject.pdf"
relationships:
  - target: "[[concepts/old-english-form-generation]]"
    type: implements
  - target: "[[concepts/old-english-inflectional-class]]"
    type: related_to
summary: >-
  CMU course report: a Xerox finite-state transducer for Old English verbs only, analysis and generation from one machine.
provenance:
  extracted: 0.70
  inferred: 0.15
  ambiguous: 0.15
base_confidence: 0.62
lifecycle: draft
lifecycle_changed: 2026-10-09
tier: supporting
created: 2026-10-09T19:50:00Z
updated: 2026-10-09T19:50:00Z
---

# A Morphological Analyzer for Old English Verbs (Adams)

Jason Adams, “A Morphological Analyzer for Old English Verbs,” 11-712 final project report, Carnegie Mellon University. [[references/tichy-2017-morphological-analyser|Tichý (2017)]] dates it 2007. The report argues that a finite-state transducer is the right machine for Old English verbs because the same network analyzes and generates, following Beesley and Karttunen (2003) and Oflazer (1994).

## Key claims

- Scope is verbs. Weak verbs (the dental preterite, about three quarters of verbs, cited from Quirk and Wrenn) and strong verbs (ablaut) are both in the network. Nouns, adjectives, and prepositions are absent.
- The upper language is the infinitive in Old English characters plus tags for person, number, tense, and mood. Indicative is the default and has no tag. An imperative tag was listed and not implemented.
- The network cited in the report has 575 states, 1,160 arcs, and 2,451 paths.
- Adams notes earlier teaching software (the Glasgow STELLA project, Kay and Smith) and treats a verb analyzer as new.

## Why it matters for a full generator

A transducer keeps generation and analysis as one description. [[concepts/old-english-form-generation|Tichý’s pipeline]] splits them: generate a form table, then look up. The FST design scales to dialect by adding flag diacritics or a separate transducer per dialect, which is the usual GiellaLT / HFST pattern, but Adams does not build that layer. ^[inferred]

## Limitations

Course project, verbs only, imperative unfinished. This page rests on the report’s abstract, introduction, and results pages as retrieved in 2026, not a line-by-line reading of the network.

Tichý’s 2017 survey also names two other partial systems this report does not replace: Verbix (Lindberg 1995), a conjugator, and MAOET (Miranda García, Triviño Rodríguez, and Calle Martín, SELIM 2000), which splits a token into prefix, lexeme, and ending dictionaries and parses them with a context-free grammar inside the CALLOE tagger (Calle Martín and Triviño Rodríguez, *Interlingüística* 9, 1998, on irregular spelling).

## Related

- [[concepts/old-english-form-generation]]
- [[concepts/old-english-inflectional-class]]
- [[entities/ondrej-tichy]]

## Sources

- [Adams, CMU 11-712 report (PDF)](http://www.cs.cmu.edu/~jmadams/NLPLabProject.pdf)
