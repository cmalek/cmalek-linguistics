---
title: >-
  Old English tooling on GitHub: landscape
category: concepts
tags: [old-english, tooling, nlp, survey]
relationships:
  - target: "[[projects/wyrdcraeft/wyrdcraeft]]"
    type: related_to
  - target: "[[concepts/nlp-corpus]]"
    type: related_to
  - target: "[[concepts/old-english-form-generation]]"
    type: related_to
sources:
  - "repo:github.com/sashaforce/oeapp"
  - "agent:wiki-ingest-github-repos-2026-10-15"
summary: "A dated review of Old English GitHub resources, with revised learner-app notes and a newer treebank-format reference."
provenance:
  extracted: 0.72
  inferred: 0.23
  ambiguous: 0.05
base_confidence: 0.5
lifecycle: draft
lifecycle_changed: "2026-10-15"
tier: supporting
created: 2026-10-15T00:00:00Z
updated: "2026-10-18T19:48:28.152600+00:00"
snapshots:
  - "[[_raw/_archived/GITHUB NHB-2018-OEstylometry 2026-10-15|GITHUB NHB-2018-OEstylometry 2026-10-15]]"
  - "[[_raw/_archived/GITHUB OldEnglishNLP 2026-10-15|GITHUB OldEnglishNLP 2026-10-15]]"
  - "[[_raw/_archived/GITHUB OldEnglishPoetryCorpus 2026-10-15|GITHUB OldEnglishPoetryCorpus 2026-10-15]]"
  - "[[_raw/_archived/GITHUB OldEnglishGlosser 2026-10-15|GITHUB OldEnglishGlosser 2026-10-15]]"
  - "[[_raw/_archived/GITHUB OEVoice 2026-10-15|GITHUB OEVoice 2026-10-15]]"
  - "[[_raw/_archived/GITHUB oe_fst 2026-10-15|GITHUB oe_fst 2026-10-15]]"
  - "[[_raw/_archived/GITHUB OldEnglish 2026-10-15 1|GITHUB OldEnglish 2026-10-15 1]]"
  - "[[_raw/_archived/GITHUB oeapp 2026-10-15|GITHUB oeapp 2026-10-15]]"
  - "[[_raw/_archived/GITHUB old_english_text_sacred_texts 2026-10-15|GITHUB old_english_text_sacred_texts 2026-10-15]]"
  - "[[_raw/_archived/GITHUB poetic_edda 2026-10-15|GITHUB poetic_edda 2026-10-15]]"
  - "[[_raw/_archived/GITHUB wyrdcraeft 2026-10-15|GITHUB wyrdcraeft 2026-10-15]]"
  - "[[_raw/_archived/GITHUB FinceptTerminal 2026-10-15|GITHUB FinceptTerminal 2026-10-15]]"
  - "[[_raw/_archived/GITHUB oeapp 2026-10-15-1|GITHUB oeapp 2026-10-15-1]]"
---

# Old English tooling on GitHub: landscape

Each repo was shallow-cloned and read, not run. README claims were checked against code. Claimed versus real purpose often differs.

## Verdicts

| Repo | Really is | Value for OE tooling | Licence |
|---|---|---|---|
| [[references/unimorph-ang]] | 178k-row paradigm table from Wiktionary | High: gold set, lookup | CC BY-SA 3.0 |
| [[references/btc-anglo-saxon]] | BT dictionary pipeline and app, verb rules with test oracle | High: design and BT parser | MIT, data PD |
| [[references/old-english-texts-iswoc]] | ISWOC treebank and annotated Beowulf | High: training and evaluation data | CC BY-NC-SA / CC BY-SA |
| [[references/echoe-corpus]] | 553k-token TEI homily corpus, no lemmas | Medium: spelling and normalisation work | GPL-3.0 |
| [[references/oldenglishmorphology-shacl]] | 13 verbs plus SHACL ablaut shapes | Medium: validation idea | Apache-2.0 |
| [[references/oe-wordnet-repos]] | Emotion-vocabulary slice, OntoLex export | Low to medium | GPL-3 / none |
| [[references/oe-dictionary-repos]] | Four dictionary-adjacent repos | Mixed | mixed |
| [[references/oldenglish-llm]] | Llama fine-tuning notebooks, no weights or data | Recipe only | none |

## Smaller or weaker repos

- **oe_fst** (sharris-umass): named FST but there is no transducer; a dictionary lookup plus suffix-regex POS guesser. It cannot run as shipped (missing data and a broken `lemmatizer.py`), and bundles DOEC-format corpus text with unclear rights. Several suffix regexes are start-anchored by mistake. MIT.
- **OldEnglishGlosser** (dylanbright): React and Vite front end sending text to Gemini in 12-line chunks with a JSON schema. No OE linguistics or verification, and the API key is baked into the client bundle. Useful only as a baseline to compare deterministic analysis against, and for its gloss-token schema.
- **OEVoice** (ryanlintott): Swift wrapper over `AVSpeechSynthesizer` that speaks IPA you supply; its value is an empirical table of Apple-voice IPA workarounds. It has no spelling-to-IPA layer, which is the missing front end (see [[concepts/old-english-pronunciation]]). MIT, v2.0.0.
- **NHB-2018-OEstylometry** (qcrit): throwaway scripts for the Neidorf et al. verse study. Character n-gram profiles, sense-pause counts, Ward clustering on 30 hand-picked n-grams, compound lookup against BT. No lemmas or POS, so it is sensitive to spelling. The tagged Calgary verse text is the useful part. No licence.
- **OldEnglishNLP** (cainesap): three R scripts preparing YCOE CoNLL-U for udpipe. Notes in comments give lemma accuracy about 0.51, XPOS 0.42. File-level train/dev/test split. No data or model. The lesson is the 255-form lemma limit and the document-level split.
- **OldEnglishPoetryCorpus** (chadmorgan): 2018 notebooks. The corpus itself is not in the repo; the DOEC SGML entity table and YCOE tag-to-POS code are the only reusable bits.
- **OldEnglish** (lrosenb2): 2017 NLTK tagger trained on dictionary headwords, unrunnable (syntax error, hardcoded paths). Nothing reusable.
- **oeapp** (sashaforce): 2018 AngularJS lesson-player skeleton, 3 lessons, no licence.
- **old_english_text_sacred_texts** (cltk): scrape of the sacred-texts poetry corpus into 127 CLTK JSON files. Line numbers are lost and the caesura survives only as spaces.
- **poetic_edda** (fjarri): Old Norse and English parallel-text typesetting pipeline (Python 2, hand-keyed XML, Gering text, Bellows 1923 translation). Its stanza and half-line XML schema, with conjecture and lacuna markup, is a model for an Old English verse layer. No licence file. See [[concepts/old-norse-grammar]].
- **wyrdcraeft** (cmalek): the user's own repo; checked against existing pages, corrections applied in [[projects/wyrdcraeft/concepts/startup-and-settings]] and [[projects/wyrdcraeft/concepts/wright-catalog]]. ADR 0022 (a planned Obsidian corpus vault of 3,115 DOE Cameron A–F entries) is not yet reflected in the vault pages. ^[inferred]
- **FinceptTerminal**: a C++20/Qt finance terminal, unrelated to Old English as a domain. Kept because its Qt architecture may inform aenglisc_toolkit; see [[references/fincept-terminal-qt-architecture]].

## Patterns across the field

- Almost none of the repos ships a licence, and the data they depend on (DOEC, YCOE, Calgary, Meelen's CoNLL-U) is restricted or external. Only btc_anglo_saxon states licences cleanly.
- Everything reuses the same [[entities/bosworth-toller|Bosworth-Toller]] scan lineage (Crist, Germanic Lexicon Project). ^[inferred]
- A generator checked against an independent oracle (btc's Wikibooks tables, SHACL shapes, unimorph/ang) is the pattern wyrdcraeft can most use.

## Additional treebank format reference

[[references/syntacticus-treebank-data]] records the newer clipping’s distinction between authoritative PROIEL XML and the CoNLL-X alternative. The README alone does not establish the collection’s exact language coverage or licensing.

## Learner-app annotation

The revised oeapp clip describes an Angular.js lesson website and pronunciation samples for æl, hwæt, lind, and “winter comes.” That observation is limited to the annotated clip; it does not establish a complete pronunciation engine. [[references/oe-dictionary-repos]] remains the separate dictionary comparison.

## Sources

- Per-repo clips in `_raw/_archived/` named `GITHUB <repo> 2026-10-15`, linked from the individual reference pages above.
- [[_raw/_archived/GITHUB NHB-2018-OEstylometry 2026-10-15]]
- [[_raw/_archived/GITHUB OldEnglishNLP 2026-10-15]]
- [[_raw/_archived/GITHUB OldEnglishPoetryCorpus 2026-10-15]]
- [[_raw/_archived/GITHUB OldEnglishGlosser 2026-10-15]]
- [[_raw/_archived/GITHUB OEVoice 2026-10-15]]
- [[_raw/_archived/GITHUB oe_fst 2026-10-15]]
- [[_raw/_archived/GITHUB OldEnglish 2026-10-15 1]]
- [[_raw/_archived/GITHUB oeapp 2026-10-15]]
- [[_raw/_archived/GITHUB old_english_text_sacred_texts 2026-10-15]]
- [[_raw/_archived/GITHUB poetic_edda 2026-10-15]]
- [[_raw/_archived/GITHUB wyrdcraeft 2026-10-15]]
- [[_raw/_archived/GITHUB FinceptTerminal 2026-10-15]]
- [[_raw/_archived/GITHUB oeapp 2026-10-15-1.md]]
