---
title: >-
  Old English lemmatisation
category: concepts
tags: [old-english, lemmatisation, nlp]
relationships:
  - target: "[[concepts/old-english-form-generation]]"
    type: related_to
  - target: "[[references/martin-arista-2026-oe-lemmatisation]]"
    type: derived_from
  - target: "[[references/computational-study-of-old-english-2025]]"
    type: derived_from
  - target: "[[entities/varioe]]"
    type: related_to
sources:
  - "url:https://huggingface.co/Nerthus-Project/Old_English_Lemmatiser"
  - "url:https://doi.org/10.3390/encyclopedia5030137"
  - "url:https://aclanthology.org/2025.acl-srw.46.pdf"
summary: >-
  Lookup generators reach mid-90s recall on known prose. Context-free neural lemmatisation on YCOE is about 68 percent.
provenance:
  extracted: 0.76
  inferred: 0.16
  ambiguous: 0.08
base_confidence: 0.73
lifecycle: draft
lifecycle_changed: 2026-10-09
tier: supporting
created: 2026-10-09T19:50:00Z
updated: 2026-10-09T19:50:00Z
---

# Old English lemmatisation

Lemmatisation assigns a dictionary headword to a token. It is not the same task as [[concepts/old-english-form-generation|generating]] the token from the headword, and the published numbers are not interchangeable.

## Lookup against a generated lexicon

[[references/tichy-2017-morphological-analyser|Tichý]] measures **recall**: did the correct analysis appear among the hits? On 2,554 words from ten texts it is 95 percent, 97.3 percent with variation filters. Precision is intentionally unmeasured. The average token still receives about two lemmas. He says disambiguation needs syntax or a learner, plus the prior that a form built with more variation steps is less likely.

[[entities/varioe|VARIOE]] (Cichosz, Pęzik, Grabski, Adamczyk, Rybińska, and Ostrowska, 2021) lemmatised [[entities/ycoe|YCOE]] by hand on top of rule-based matching, using DOE A–I and Bosworth–Toller. The online morphological dictionary (`varioe.pelcra.pl/morph`) lists the attested forms of a lemma with frequencies, and the reverse lookup from form to lemma. [[references/computational-study-of-old-english-2025|Martín Arista (2025)]] reports about 30,000 lemmas and accuracy over 95 percent for that project. The frequency-dictionary preface confirms the method and warns that spelling variants of one meaning were merged, at a cost in morphological precision. The 95 percent figure is the survey’s.

CLTK’s `OldEnglishDictionaryLemmatizer` is a dictionary join over an inverted lemma list shipped in `ang_models_cltk`, with unigram frequencies as a tie-break. It does not generate forms and it does not see context beyond that frequency.

## Neural, context-free

[[references/martin-arista-2026-oe-lemmatisation|Martín Arista (2026)]] trains a character-level Transformer on YCOE triples. Test lemma accuracy is **67.58 percent**, UPOS **82.75 percent**. Gold inconsistency is 11.3 percent of types, and the card treats human agreement around 90–95 percent as the ceiling. Errors concentrate on strong-verb ablaut, spelling, and *ge-*. The model never emits stem class or case.

The gap between “95 percent recall of a dictionary match” and “68 percent exact lemma” is mostly the task. Tichý scores a hit if the right pair is in the list. The Transformer must emit one string, on YCOE spellings, with no sentence. ^[inferred]

## Poetry

Hamdoun Bghiyel’s poetry lemmatisation, as reported in the 2025 encyclopedia, assigned existing ParCor lemmas to 99 percent of YCOEP forms and invented 72 lemmas, mostly compounds. Automatic assignment covered 73 percent of types before the manual remainder. [[references/miani-2025-oe-poetry-pos|Miani, Stymne, and Darwin (2025)]] show the POS side of the same split: a prose tagger does not become a poetry tagger by seeing more prose. Their only cited off-the-shelf Old English tagger is CLTK’s, trained on the small ISWOC sample, accuracy unknown.

ISWOC / PROIEL annotation, which that tagger uses, does carry case, number, gender, tense, mood, and a strong/weak strength feature. The Old English slice is a few short texts (Ælfric, Apollonius, the Chronicle, Orosius, the West Saxon Gospels), on the order of tens of thousands of tokens, not YCOE’s 1.5 million words.

## Homographs

The encyclopedia’s example is *bær*, either a form of *beran* or the adjective *bǣr*. Tichý, the YCOE manual, and the 2026 model card agree that morphology or a context-free model will not finish that choice. Government and word order are the next layer. See [[concepts/old-english-case-government]].

## Related

- [[concepts/old-english-form-generation]]
- [[concepts/old-english-inflectional-class]]
- [[entities/varioe]]
- [[entities/ycoe]]

## Sources

- [[references/tichy-2017-morphological-analyser]]
- [[references/martin-arista-2026-oe-lemmatisation]]
- [[references/computational-study-of-old-english-2025]]
- [[references/miani-2025-oe-poetry-pos]]
