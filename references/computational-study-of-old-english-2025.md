---
title: >-
  The Computational Study of Old English (2025)
category: references
tags: [old-english, corpus, survey]
sources:
  - "url:https://doi.org/10.3390/encyclopedia5030137"
source_url: "https://www.mdpi.com/2673-8392/5/3/137"
relationships:
  - target: "[[concepts/old-english-lemmatisation]]"
    type: related_to
  - target: "[[entities/dictionary-of-old-english]]"
    type: related_to
  - target: "[[entities/varioe]]"
    type: related_to
  - target: "[[entities/nerthus-project]]"
    type: related_to
summary: >-
  Martín Arista’s 2025 encyclopedia map of OE corpora, dictionaries, lemmatisation, treebanks, and neural tools.
provenance:
  extracted: 0.80
  inferred: 0.12
  ambiguous: 0.08
base_confidence: 0.60
lifecycle: draft
lifecycle_changed: 2026-10-09
tier: supporting
created: 2026-10-09T19:50:00Z
updated: 2026-10-09T19:50:00Z
---

# The Computational Study of Old English (2025)

Javier Martín Arista, “The Computational Study of Old English,” *Encyclopedia* 5, no. 3 (2025): 137, https://doi.org/10.3390/encyclopedia5030137. Published 4 September 2025. It is a survey by the director of [[entities/nerthus-project|Nerthus]], so project-internal numbers and outside projects sit in one voice. Where a figure below is his report of someone else’s dissertation, this page says so.

## Resources he lines up

- Helsinki Corpus: about 413,000 Old English words, periods O1–O4, metadata for genre, dialect, and date.
- Dictionary of Old English Corpus: about 3,000 texts and 3 million words. The [[entities/dictionary-of-old-english|DOE]] itself, in this entry, covers **A–Le**. A sample entry shape is headword, gender, a FORM line of attested spellings by case and number, frequency, senses, compounds, and collocations.
- [[entities/ycoe|YCOE]]: 1.5 million words of prose with POS and phrase structure. His gloss of a sample tag string treats `NSD` as noun, singular, dative and `VPS` as verb, past, singular, third person.
- Dictionary sizes, cited at second hand from Ellis: Bosworth about 26,000 entries with normalized West Saxon and acknowledged variants; Sweet about 12,000 with strict late West Saxon; Clark Hall about 35,000 with mixed normalization. These counts describe nineteenth-century editions, not the online Bosworth–Toller after Toller and not Nerthus v5’s 32,812 files. ^[ambiguous]
- West Saxon is about 60 percent of surviving material. Religious and legal texts are about 70 percent of the DOEC. Late Old English (after 950) outweighs earlier centuries. Models trained on the corpus inherit that skew.

## Lemmatisation he reports

- Metola Rodríguez, strong verbs in the DOEC: about **80 percent** lemma identification before manual revision. Query strings target stem, inflection, and prefix. Class II *bēodan* is the example (*bēad*, *budon*, kept apart from homographic nouns).
- García Fernández: preterite-present, contracted, anomalous, and strong class VII, aimed at letters I–Y where the DOE had not yet published.
- Tío Sáenz: weak verbs, the productive majority. Non-canonical spellings such as *gærwod* and *gegarwed* beside *gearwode*.
- [[entities/varioe|VariOE]] (Cichosz et al. 2021): a lemmatised YCOE, about **30,000 lemmas**, accuracy he states as **over 95 percent**. Lemmas follow DOE A–I and Bosworth–Toller. Spelling variants of one meaning were collapsed to one lemma, which he says trades morphological precision for phraseological recall. The primary frequency-dictionary preface confirms the manual workflow and the online morphological dictionary at `varioe.pelcra.pl/morph`. The “over 95 percent” figure is this encyclopedia’s, not a number printed in the preface pages read for this note.
- Hamdoun Bghiyel, YCOEP poetry, aligned to Nerthus / ParCor: automatic lemma assignment for **73 percent** of unique attested forms. Function words above 95 percent. **72 new lemmas**, mostly compounds absent from the DOE (28 nouns, 19 adjectives, 11 verbs, 13 others), against about 7,000 lemmas and 69,456 attested forms. **99 percent** of forms received an existing ParCor lemma. **1 percent** needed a new one.

That 1 percent is the quantitative shape of “poetry compounds missing from the dictionary.” It is small as a fraction of tokens and real as a list of lemmas a closed generator will never emit.

## Related

- [[concepts/old-english-lemmatisation]]
- [[concepts/old-english-form-generation]]
- [[references/nerthus-v5-database]]
- [[references/martin-arista-2026-oe-lemmatisation]]

## Sources

- [Encyclopedia 2025, 5(3), 137](https://doi.org/10.3390/encyclopedia5030137)
