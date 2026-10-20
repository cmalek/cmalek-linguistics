---
title: >-
  old-english-texts (ISWOC and Beowulf)
category: references
tags: [old-english, corpus, treebank]
relationships:
  - target: "[[entities/ycoe]]"
    type: related_to
  - target: "[[concepts/nlp-corpus]]"
    type: related_to
sources:
  - "repo:github.com/old-english-learner-texts/old-english-texts"
source_url: "https://github.com/old-english-learner-texts/old-english-texts"
summary: >-
  Data repo bundling the ISWOC Old English treebank (5 prose texts, about 30k tokens, CoNLL and PROIEL XML) and a lemmatised, macronised Brunetti Beowulf table.
provenance:
  extracted: 0.85
  inferred: 0.1
  ambiguous: 0.05
base_confidence: 0.5
lifecycle: draft
lifecycle_changed: "2026-10-15"
tier: supporting
created: 2026-10-15T00:00:00Z
updated: 2026-10-15T00:00:00Z
snapshots:
  - "[[_raw/_archived/GITHUB old-english-texts 2026-10-15|GITHUB old-english-texts 2026-10-15]]"
---

# old-english-texts (ISWOC and Beowulf)

James Tauber's data-only repo (about 12 MB). The README promises more than exists: Alfred's *Pastoral Care* preface has only Sweet's transcriptions and a translation, and the "normalization, lemmatization, tagging coming soon" never arrived. The Beowulf README mentions an `aligned.txt` that is not present.

## Contents

- **`ISWOC/`**: five texts (`æls`, `apt`, `chrona`, `or`, `wscp`) as PROIEL-XML (schema 2.1, exported 2018-04-01) and CoNLL. About 30.8k CoNLL lines. Columns: id, form, lemma, coarse POS, fine POS, morphology (`NUMBs|GENDf|CASEn`), head, relation. Dependency labels are PROIEL's (`sub`, `atr`, `adv`, `pred`).
- **`beowulf/beowulf_annotations.csv`**: about 17k tokens with `ve_ref, token_w_punct, token, lemma, syntax, modern_english, morphology`. Derived from Brunetti's analysis, with vowel lengths added from the Perseus text. Token IDs like `0003a2` encode line, half-line, and offset. The only code is a pandas notebook, `make-brunetti-tsv.ipynb`.
- **`thorpe/`**: corrected OCR of Thorpe's translation.

## Licence

ISWOC is **CC BY-NC-SA 3.0** (non-commercial); the rest is CC BY-SA 4.0. Last commit 2023-02-14, no tests.

## Value

The treebank is the most useful asset: lemma, POS, morphology, and dependencies across West Saxon and Anglian prose, ready for training or evaluation. Brunetti's table is a lexicon seed and a paradigm test set with vowel length. Both are pre-existing, widely mirrored data. Tagsets are idiosyncratic and some lemmas are unnormalised (`Gar-Dene`). Compare with [[entities/ycoe]] and see [[references/echoe-corpus]] for an unannotated prose corpus.

## Sources

- [[_raw/_archived/GITHUB old-english-texts 2026-10-15]]
- Repo read directly on 2026-10-15 (shallow clone, nothing executed).
