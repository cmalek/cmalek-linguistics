---
title: >-
  Morphological Analyser of Old English (Tichý 2017)
category: references
tags: [old-english, morphology, computational-linguistics]
sources:
  - "url:https://casopispromodernifilologii.ff.cuni.cz/wp-content/uploads/sites/9/2017/06/Ondřej_Tichý_40-54.pdf"
source_url: "https://casopispromodernifilologii.ff.cuni.cz/wp-content/uploads/sites/9/2017/06/Ondřej_Tichý_40-54.pdf"
relationships:
  - target: "[[concepts/old-english-form-generation]]"
    type: implements
  - target: "[[concepts/old-english-inflectional-class]]"
    type: related_to
  - target: "[[concepts/old-english-orthographic-variation]]"
    type: related_to
  - target: "[[entities/ondrej-tichy]]"
    type: related_to
  - target: "[[entities/bosworth-toller]]"
    type: uses
summary: >-
  Tichý 2017 generates BT lemmas from Wright paradigms. Recall is 95 percent, 97.3 with dialect filters, on 2,554 words.
provenance:
  extracted: 0.78
  inferred: 0.12
  ambiguous: 0.10
base_confidence: 0.67
lifecycle: draft
lifecycle_changed: 2026-10-09
tier: supporting
created: 2026-10-09T19:50:00Z
updated: 2026-10-09T19:50:00Z
---

# Morphological Analyser of Old English (Tichý 2017)

Ondřej Tichý, “Nástroj na tvaroslovnou analýzu staré angličtiny” (*Journal of Modern Philology* 99, no. 1 (2017): 40–54). The article summarizes an unpublished 2014 Charles University thesis of the same name. Claims below are taken from a machine translation of the Czech article, checked against the tables. The English thesis abstract on ResearchGate repeats the 95 percent recall figure.

The tool has three stages. A base dictionary of lemmas carries part of speech and class. A generator expands each lemma through an assigned paradigm. An analyzer matches a token to that form list. Disambiguation is declared out of scope: morphology alone cannot choose among homonyms.

## Key claims

- The lemma list is [[entities/bosworth-toller|Bosworth–Toller]] (1921), chosen because it is the only dictionary that, in Tichý’s words, at least theoretically covers the whole Old English lexicon. Wright and Wright, *Old English Grammar* (1914), supplies exemplar paradigms. Campbell’s grammar was set aside on licensing grounds so the extracted class data could sit on bosworthtoller.com.
- Traditional seven strong classes, three weak classes, and a handful of preterite-present and irregular verbs are replaced, for the machine, by **132 verb classes**. See [[concepts/old-english-inflectional-class]].
- Generation is lemma-based. Nouns and adjectives are mostly lemma plus ending. Verbs need exemplar stems because ablaut is not recoverable from the infinitive alone. Pronouns and some irregular verbs are hand-inflected.
- Loading normalizes thorn and eth, keeps macronized and bare lemma pairs (length marks are editorial), and computes syllable count and stem length for class assignment.
- Paradigm assignment compares the lemma string with exemplar lemmas, then falls through to rules.
- Full dialect-by-period generation was rejected. Variation filters (simple swaps such as *u*/*v*, and regular expressions such as back vowels before nasals, drawn from Baker 2012 and Wright) run at match time, and the user can turn them on by the age and dialect of the text. See [[concepts/old-english-orthographic-variation]].
- Table 5, ten excerpts, 2,554 words: mean recall **95 percent**, **97.3 percent** with filters. Late West Saxon prose sits at the ceiling (Gospel excerpts 100 percent; Ohthere and Wulfstan 99.4; Cynewulf and Cyneheard 99; Ælfric 98.6; Wulfstan 97.1 / 97.8). Beowulf 96.8 / 98.4. Rushworth Gospels (Mercian) 94.6 / 97. Lindisfarne Gospels (Northumbrian) 89.6 / 90.7. Oswulf’s charter (Kentish, 806) 84.7 / 94.2.
- Table 6: **70,914 lemmas**, **11,443,596** generated forms, **2,095,844** unique strings. Nouns 19,835 lemmas (masculine 8,668, feminine 7,306, and a third gender row of 4,067, the neuter count in a three-way split). ^[inferred] Verbs 6,959 (weak 5,094, strong 1,786, preterite-present 32, irregular 59). Adjectives average about 302 generated forms and 47 unique forms per lemma.
- Overgeneration is cut by intersecting the form list with the Dictionary of Old English Corpus (Healey et al. 2000). Unattested cells are discarded because, Tichý argues, the surviving corpus is essentially closed.
- A matched token still averages about two lemmas and several dozen morphological readings. The worked example *andswarodon* is plural indicative preterite of weak class 2, subtype a, lemma *and-swarian*, pattern *sealfian*.

## What the misses are

Residual errors are forms the rules will not predict: scribal errors, and dialect or period spellings that were left out of generation because a full cartesian product would make the form dictionary unusable. Those tokens are left for manual disambiguation.

Prefixed verbs are lemmas in this design. The article’s running example is *æt-swymman*. A generator that strips prefixes off headwords before class assignment will drop lemmas this system kept. ^[inferred]

## Limitations

The test is 2,554 words, not the corpus. Recall ignores false analyses. The Czech tables passed through machine translation, so row labels for participles and the third noun gender are less secure than the integers. The live analyzer was a PHP/MySQL application beside the online dictionary and was not public in 2017. Perl scripts build the form list. That Perl generator is the ancestor of [[projects/wyrdcraeft/concepts/morphology-generation]].

## Related

- [[concepts/old-english-form-generation]]
- [[concepts/old-english-lemmatisation]]
- [[references/adams-2007-oe-verb-analyzer]]
- [[references/computational-study-of-old-english-2025]]

## Sources

- [Tichý 2017 PDF](https://casopispromodernifilologii.ff.cuni.cz/wp-content/uploads/sites/9/2017/06/Ondřej_Tichý_40-54.pdf)
- Local copy used for this page: `wordwending/sources/Ondej_Tich_40-54-1.pdf` (Google translation of the same article)
