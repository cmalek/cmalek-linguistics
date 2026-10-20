---
title: >-
    Old English Lexicon Size and Missing Vocabulary
category: concepts
tags: [old-english, lexicography, vocabulary, corpus-linguistics]
relationships:
  - target: "[[entities/bosworth-toller]]"
    type: uses
  - target: "[[entities/dictionary-of-old-english-corpus]]"
    type: uses
  - target: "[[entities/nerthus-project]]"
    type: related_to
  - target: "[[concepts/old-english-lemmatisation]]"
    type: related_to
sources:
  - "agent:chat-notes Old English Lexicon Size and Missing Vocabulary Conversation"
summary: "Why counts of OE words (23k, 40k, 62k, 3M tokens, 17M generated forms) measure different things, a prior of 20-35k known lexemes, and five methods for finding unattested words."
provenance:
  extracted: 0.50
  inferred: 0.45
  ambiguous: 0.05
base_confidence: 0.42
lifecycle: draft
lifecycle_changed: "2026-10-17"
tier: supporting
created: 2026-10-17T12:10:00Z
updated: 2026-10-17T12:10:00Z
snapshots:
  - "[[_raw/_archived/Old English Lexicon Size and Missing Vocabulary Conversation|Old English Lexicon Size and Missing Vocabulary Conversation]]"
---

# Old English Lexicon Size and Missing Vocabulary

Research framing distilled from a long chat note. All figures are secondary claims relayed in that note, not verified here. Motivating questions: which words that must have existed are unattested (animals, plants, tools, household items), and how many words an educated Anglo-Saxon knew.

## Key Ideas

**Modern benchmarks.** Active vocabulary of an adult is roughly 3,000-10,000 lemmas; strict receptive knowledge about 17,000 base words (Goulden, Nation and Read 1990); permissive recognition about 42,000 lemmas at age 20 and 48,000 at 60 (Brysbaert et al. 2016). The oft-quoted 200,000 comes from counting inflections, derivatives, compounds and names. For "recognise and roughly define", the note uses 20,000-40,000. The full communal Modern English lexicon is put at 500,000-1,000,000 (OED about 600,000 words; Oxford current English over 350,000; Merriam-Webster about one million, with large error), so an educated individual knows perhaps 5-10%.

**Three quantities to keep apart for OE:** the attested lexicon, the communal lexicon (everything conventional in the speech community), and an individual's mental lexicon.

**Why the counts disagree.**

| Figure | What it actually counts |
|---|---|
| 23,000-24,000 | Kastovsky's rough scholarly count of lexical items |
| about 32,800 | Headword files in [[entities/nerthus-project]] (mainly Clark Hall) |
| just over 40,000 | Part-of-speech entries in online [[entities/bosworth-toller]], including variants |
| 62,745 | Machine-recognised B-T headword records (Faulkner 2023) |
| about 3 million | Running tokens in [[entities/dictionary-of-old-english-corpus]] (plus about 1 million Latin words), not distinct forms |
| 14.5 million | Forms a morphologiser generated from the 62,745 records (Faulkner); 115 million with three spelling alternations |
| 17 million | Entries from the user's own morphology generator, a model's capacity rather than stored words |

Bosworth-Toller is a layered print artefact: the 1898 main volume and 1921 supplement are separate source layers, and supplement records may add a sense, add citations, correct, record a variant or inflected form, or merely cross-refer. No defensible "unique entries" figure exists; the note proposes a reconciliation table with relations such as SUPPLEMENTS, VARIANT_OF, INFLECTED_FORM_OF, SAME_LEMMA_AS and counts at the levels entry record, headword string, lemma, lexeme, word family. A composite entry per normalised lemma (Bosworth, Toller supplement, Campbell addenda, redirects) is the desired interface; see [[references/oe-dictionary-repos]] and [[concepts/old-english-lemmatisation]]. ^[inferred]

**Prior for an educated Anglo-Saxon:** about 20,000-35,000 lexemes (plausible 15,000-40,000), explicitly a research prior and not a result. Reasoning: same cognitive capacity as moderns; richer ecological, craft and kinship vocabulary than texts show; productive compounding ([[concepts/oe-word-formation]]) reduces stored items; Latin lexicon would be additional. The note suggests a reference persona: a literate West Saxon ecclesiastic c. 975-1025 with functional Latin. The overlap with the dictionary inventory is partly accidental. ^[inferred]

**Five methods for candidate unattested words** (graded evidence, not a flat "missing words" list):

1. Semantic-domain gaps against the Thesaurus of Old English (empty or generic-only categories where the referent was salient).
2. Material-culture alignment with archaeology (tools, crops, textiles, ships).
3. Comparative Germanic evidence (Frisian, Saxon, High German, Norse cognates, regular sound correspondences, no known OE replacement); see [[concepts/germanic-language-family]].
4. Morphological paradigm gaps (agent nouns, tool names, privatives), separating "could be understood", "probably conventional" and "inherited".
5. Statistical unseen-vocabulary estimators (hapax-based), only within controlled subcorpora and as lower bounds.

Evidence labels suggested: inherited with high confidence, probable West Germanic formation, possible native formation, transparent hypothetical coinage.

**Suggested reading** (from the note): Kastovsky "Semantics and Vocabulary" (CHEL 1); Nation and Coxhead 2021; Brysbaert et al. 2016; Roberts and Kay, *A Thesaurus of Old English*; DOE/DOEC; Nerthus; Cichosz et al. 2022 frequency dictionary; Faulkner 2023; Baayen 2001; Bhat and Sproat 2009; Kroonen 2013; Ringe and Taylor 2014; Biggam and Bierbaumer on plant names (336 native botanical names); Banham and Faith on farming. Plants then farming tools recommended as pilot domains.

## Open Questions

- What is the true number of distinct lemmas and lexemes in Bosworth-Toller after merging supplement records?
- How large is the unseen OE lexicon in a given genre and dialect?

## Sources

- [[_raw/_archived/Old English Lexicon Size and Missing Vocabulary Conversation]]
