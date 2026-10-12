---
title: >-
  Old English form generation
category: concepts
tags: [old-english, morphology, generation]
relationships:
  - target: "[[references/tichy-2017-morphological-analyser]]"
    type: derived_from
  - target: "[[references/adams-2007-oe-verb-analyzer]]"
    type: related_to
  - target: "[[references/nerthus-v5-database]]"
    type: related_to
  - target: "[[projects/wyrdcraeft/concepts/morphology-generation]]"
    type: related_to
sources:
  - "url:https://casopispromodernifilologii.ff.cuni.cz/wp-content/uploads/sites/9/2017/06/Ondřej_Tichý_40-54.pdf"
  - "url:http://www.cs.cmu.edu/~jmadams/NLPLabProject.pdf"
  - "url:https://www.nerthusproject.com/database-description"
summary: >-
  Published OE generators expand a closed lemma list through class paradigms, then drop cells the corpus does not attest.
provenance:
  extracted: 0.72
  inferred: 0.22
  ambiguous: 0.06
base_confidence: 0.74
lifecycle: draft
lifecycle_changed: 2026-10-09
tier: supporting
created: 2026-10-09T19:50:00Z
updated: 2026-10-09T19:50:00Z
---

# Old English form generation

A form generator turns a lemma plus a class into the inflected strings of that lemma. Analysis is the inverse: a string in a text is matched back to one or more lemma-and-tag pairs. The published Old English systems do the first job in order to do the second, and they are built for texts that already exist.

## The working design

[[references/tichy-2017-morphological-analyser|Tichý (2017)]] is the only published full-lexicon generator. Lemmas come from [[entities/bosworth-toller|Bosworth–Toller]]. Class and exemplar paradigms come from Wright and Wright (1914). The machine uses 132 verb classes rather than the textbook ten. Generation is from the lemma, not from a reconstructed root. Thorn and eth are unified. Macrons are kept as a parallel lemma, because manuscripts do not write them. The result he prints is 70,914 lemmas, 11.4 million generated forms, and 2.1 million unique strings.

[[references/adams-2007-oe-verb-analyzer|Adams]] showed the same job for verbs alone as one Xerox transducer, so generation and analysis are the same network. He did not attach a dictionary of the whole lexicon.

[[references/nerthus-v5-database|Nerthus v5]] also generates canonical inflectional forms, and it keeps the forms that are attested in the Dictionary of Old English Corpus. v3 already stored alternative spellings and an inflectional-class label such as “strong III.”

[[projects/wyrdcraeft/concepts/morphology-generation|wyrdcraeft]] is a Python port of Tichý’s generator, judged in that project against grammar references rather than against the Perl output.

## Two filters that define the product

Tichý intersects the generated list with the DOEC and throws away unattested cells. He can do that because he treats the surviving corpus as closed. Nerthus v5’s generated list is the same kind of object: canonical forms that happen to be attested.

He also refuses to generate the full dialect-by-period cartesian product. Dialect spelling is a **filter at match time**, selectable by the user, not a label on each cell. Recall on his 2,554-word sample is 95 percent, and 97.3 percent with filters. Late West Saxon prose is at the ceiling. The Kentish charter and the Northumbrian gloss are the floor. See [[concepts/old-english-orthographic-variation]].

A generator whose purpose is every grammatical cell, including cells no manuscript shows, and including compounds no dictionary has entered, is a different product from either of those systems. ^[inferred]

## Compounds and prefixes

Both Tichý and Nerthus treat a prefixed or compound word as a **headword**, not as something the generator assembles. Tichý’s worked verb is *æt-swymman*. Nerthus records compounding and affixation as derivational processes, and it allows only 65 hypothetical predicates, each of which must rest on an attested process. [[references/computational-study-of-old-english-2025|Martín Arista (2025)]] reports that a poetry lemmatisation against that inventory still needed 72 new lemmas, mostly compounds, about 1 percent of poetic forms.

The inflection of a new compound follows the class of its morphological head. In [[concepts/oe-word-formation|Mitchell’s account]] the first element is usually uninflected, which is the surface of that rule. ^[inferred] A generator that strips prefixes and hyphens before class assignment will miss lemmas the dictionaries entered as prefixed headwords. ^[inferred]

MAOET (Calle Martín and colleagues, 2000) is the older design that splits prefix, lexeme, and ending into separate dictionaries. Nobody has published that split as a full productive grammar over Bosworth–Toller. ^[inferred]

## What to build on

For lemmas that are already in a dictionary, the class-and-paradigm method is the one with measured recall, and the measured recall is on analysis of known texts, not on novel words. For words that are not in the dictionary, the missing piece is a segmenter plus the head’s [[concepts/old-english-inflectional-class|inflectional class]], not a larger neural lemmatiser. The 2026 character-level lemmatiser predicts a lemma string and a UPOS tag. It does not emit a paradigm.

## Related

- [[concepts/old-english-inflectional-class]]
- [[concepts/old-english-lemmatisation]]
- [[concepts/old-english-orthographic-variation]]
- [[synthesis/Research: Old English Morphology Generation]]

## Sources

- [[references/tichy-2017-morphological-analyser]]
- [[references/adams-2007-oe-verb-analyzer]]
- [[references/nerthus-v5-database]]
- [[references/computational-study-of-old-english-2025]]
