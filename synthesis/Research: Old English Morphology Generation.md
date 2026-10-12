---
title: >-
  Research: Old English Morphology Generation
category: synthesis
tags: [old-english, morphology, lexicography, dialects, research]
relationships:
  - target: "[[concepts/old-english-form-generation]]"
    type: related_to
  - target: "[[concepts/old-english-inflectional-class]]"
    type: related_to
  - target: "[[concepts/old-english-case-government]]"
    type: related_to
  - target: "[[concepts/old-english-orthographic-variation]]"
    type: related_to
  - target: "[[concepts/old-english-lemmatisation]]"
    type: related_to
  - target: "[[projects/wyrdcraeft/concepts/morphology-generation]]"
    type: related_to
sources:
  - "url:https://casopispromodernifilologii.ff.cuni.cz/wp-content/uploads/sites/9/2017/06/Ondřej_Tichý_40-54.pdf"
  - "url:https://www.nerthusproject.com/database-description"
  - "url:https://huggingface.co/Nerthus-Project/Old_English_Lemmatiser"
  - "url:https://www-users.york.ac.uk/~lang18/Documentation/pos-manual-oe.htm"
  - "url:https://paveda.unipv.it/contributions/olde1238"
  - "url:https://doi.org/10.3390/encyclopedia5030137"
  - "url:https://aclanthology.org/2025.acl-srw.46.pdf"
summary: >-
  Three-round survey: class lives in Nerthus and Tichý, government in PaVeDa’s 80 verbs, and no generator labels full dialect paradigms.
provenance:
  extracted: 0.68
  inferred: 0.22
  ambiguous: 0.10
base_confidence: 0.78
lifecycle: draft
lifecycle_changed: 2026-10-09
tier: supporting
created: 2026-10-09T19:50:00Z
updated: 2026-10-12T04:37:00Z
---

# Research: Old English Morphology Generation

## Overview

The published toolkit splits in two, and neither half is a full generator of every grammatical word. Dictionary-driven generators, above all [[entities/ondrej-tichy|Ondřej Tichý]]’s analyser and the [[entities/nerthus-project|Nerthus]] database, expand a closed headword list through inflectional class and then keep the forms a corpus attests. Corpus taggers and lemmatisers, from [[entities/ycoe|YCOE]] through [[entities/varioe|VARIOE]] to the 2026 character-level Transformer, identify part of speech on tokens and do not emit a paradigm, a stem class, or a dialect label. Case government exists as a small valency sample, not as a feature of those generators. Novel compounds and unattested dialect cells are the part of the problem the field has measured and then left outside the generator.

[[projects/wyrdcraeft/concepts/morphology-generation|wyrdcraeft]] sits in the first family. Its recall on ordinary prose lemmas is the expected strength. Its misses on prefixed and compound lemmas are the expected hole.

## Key Findings

- **Part of speech is a lexical field on the headword, and a tagging problem on the token.** Nerthus v5 stores lexical category together with inflectional class ([[references/nerthus-v5-database]]). Tichý exports the same pair from Bosworth–Toller plus Wright ([[references/tichy-2017-morphological-analyser]]). On tokens, YCOE’s tagset is hundreds of labels and marks case when the ending shows it ([[references/ycoe-case-and-pos-annotation]]). Mapping those tags to Universal Dependencies keeps 17 categories and drops case, gender, and number ([[references/miani-2025-oe-poetry-pos]]). The 2026 lemmatiser’s UPOS accuracy on a YCOE held-out split is 82.75 percent, with verbs near 55 percent ([[references/martin-arista-2026-oe-lemmatisation]]).
- **Stem class is solved for dictionary lemmas and unsolved for new compounds.** Nerthus copies class from Clark Hall, Bosworth–Toller, and Sweet, and uses Krygier (1994) for strong-verb subclasses. The sample label is “strong III.” Tichý explodes the textbook verb list into 132 machine classes and assigns them by matching exemplar lemmas, then by syllable count and stem length. A UPOS tag never carries this. For a compound the dictionaries have not entered, class has to come from the morphological head. Mitchell’s description of compounds, the first element usually uninflected, is the surface of that rule ([[concepts/oe-word-formation]]). ^[inferred]
- **The lemma list is the ceiling.** Tichý’s Table 6 has 70,914 lemmas and 11.4 million generated forms. Nerthus v5 has 32,812 headword files. Clark Hall is the spelling standard for Nerthus. Bosworth–Toller is the only complete older dictionary. The DOE writes from the [[entities/dictionary-of-old-english-corpus|DOEC]]. Its own A to Le page (2024) is the published online edition; the 2025 progress report still has Li–Ly in draft. Nerthus links DOE headwords only for A–I. The DOEC is the attestation check under those entries, and it is not itself a lemma list ([[skills/using-doec]]). Poetry lemmatisation against Nerthus still needed 72 new lemmas, mostly compounds, about 1 percent of YCOEP forms ([[references/computational-study-of-old-english-2025]]). Nerthus allows only 65 hypothetical derivatives, each tied to an attested process. A productive compound generator has not been published.
- **Prefixes are lemmas, and *ge-* is special.** Tichý generates *æt-swymman* as a headword. Nerthus’s simplex form drops *ge-*. The 2026 model’s errors are about 15 percent *ge-*, 25 percent strong-verb ablaut, and 20 percent spelling. MAOET (Calle Martín and colleagues, 2000) is the older system that stored prefixes in their own dictionary. A pipeline that strips prefixes before class assignment will drop headwords these lexicons kept. ^[inferred]
- **Case government is not in the generator.** YCOE refuses to label an ambiguous object from the verb or preposition that governs it, except for a dative default when the governor is not on Mitchell’s genitive list. [[entities/paveda|PaVeDa]] codes real frames, including preposition plus case, for the 80 ValPaL meanings only ([[references/paveda-old-english-valency]]). There is no public frame lexicon for the rest of Bosworth–Toller. Prefixed verbs do not inherit the simplex frame unchanged. Ruiz Narbona’s Nerthus papers treat *ā-*, *for-*, and *ge-* as transitivity changes.
- **Dialect is a filter or an attested list, not a labeled paradigm.** Tichý’s recall on 2,554 words is 95 percent, 97.3 percent with match-time variation filters. Late West Saxon prose is at the ceiling. A Kentish charter of 806 is 84.7 percent, 94.2 with filters. The Northumbrian Lindisfarne gloss is 89.6, and filters barely move it (90.7). He refused to generate the dialect-by-period cartesian product because the form dictionary would become unusable. He also deletes unattested cells by intersecting with the DOEC, on the view that the corpus is closed. That choice is right for tagging surviving texts and wrong for emitting grammatical forms of words the corpus never shows. ^[inferred]
- **The 95 percent and the 68 percent do not contradict.** Tichý scores recall: the correct analysis is somewhere in the hit list, and the average token still has about two lemmas. The Transformer must emit one lemma string with no context. VARIOE’s “over 95 percent,” as the 2025 survey states it, is manual lemmatisation of YCOE prose, with spelling variants of one meaning sometimes collapsed ([[entities/varioe]]).
- **Poetry is a second domain, not a longer prose sample.** Extra YCOE prose does not by itself raise poetry POS accuracy. A little poetry training data does ([[references/miani-2025-oe-poetry-pos]]). The only off-the-shelf tagger those authors cite is CLTK’s, trained on the small ISWOC treebank, accuracy unknown.

## What each goal can use now

**Identify part of speech.** For a headword, copy Nerthus or the dictionary. For a token in prose, VARIOE plus YCOE tags, or the 2026 model if a single UPOS guess is enough. For poetry, train on poetry. Expect homographs (*bær* as *beran* or *bǣr*) to stay ambiguous without syntax.

**Identify class.** Copy Nerthus’s inflectional-class field, or Tichý’s 132 verb classes where the port already has them. Krygier 1994 is the strong-verb subclass authority Nerthus names. DOE gender and strong/weak are coarser and only for the published letters. New compounds: segment, take the class of the right-hand head, and treat *ge-* as optional on that same class. Guest search of the live file is [[skills/using-nerthus]].

**Identify the case a verb or preposition governs.** Start from PaVeDa’s 80 frames and from the genitive-verb list YCOE borrowed from Mitchell, *Old English Syntax* (1985). Do not mine YCOE’s case labels as if they were government. Budget a separate lexicon for the rest, and do not copy a simplex frame onto a prefixed verb without checking.

**Generate every form in the main dialects, with the dialect identified.** Generate a late West Saxon canonical paradigm from the class, which is what Wright, Bosworth–Toller, Sweet, and Tichý already approximate. Apply named correspondence rules as a second layer, using the cues already gathered under [[concepts/old-english-dialects]], and label the layer. Keep DOE and DOEC spellings as a third, attested layer, distinct from the generated one. The Web Corpus is how that third layer is searched ([[skills/using-doec]]). Expect Anglian noun endings, not only vowels, to differ (Adamczyk on i-stems). Expect Northumbrian glosses to resist a West Saxon filter set, as Tichý’s Lindisfarne number shows. No published system emits this three-layer object. ^[inferred]

**Other expected variants.** Thorn/eth, editorial macrons, *u*/*v*, back vowels before nasals, and the *i*/*y* and *æ*/*a*/*e* swaps the 2026 model augments with. Tichý’s filters are the explicit list. Scribal errors stay outside generation, by his own cutoff.

## Core Concepts

- [[concepts/old-english-form-generation]] — closed lemma list, class, paradigm, then attestation filter.
- [[concepts/old-english-inflectional-class]] — the lexical field taggers drop.
- [[concepts/old-english-case-government]] — YCOE’s refusal and PaVeDa’s 80 frames.
- [[concepts/old-english-orthographic-variation]] — filters and attested spellings, not labeled dialect paradigms.
- [[concepts/old-english-lemmatisation]] — why 95 percent recall and 68 percent exact match are different tasks.
- [[concepts/old-english-dialects]] — the spelling cues a variant layer can be built from.
- [[concepts/oe-word-formation]] — compounds and prefixes as the missing lemma factory.
- [[concepts/old-english-grammar]] — the classroom paradigms those classes refer to.
- [[projects/wyrdcraeft/concepts/morphology-generation]] — the Python port of Tichý.
- [[projects/wyrdcraeft/concepts/wright-catalog]] — class labels already attached at generation time.

## Entities and Tools

- [[entities/ondrej-tichy]] — the full-lexicon generator and the online Bosworth–Toller.
- [[entities/bosworth-toller]] — the lemma list Tichý judged the only complete one. Campbell’s 1972 addenda are not in the online edition.
- [[entities/nerthus-project]] — class, derivation, alternative spellings, ParCorOE. How to open the guest search: [[skills/using-nerthus]].
- [[entities/javier-martin-arista]] — Nerthus and the 2026 lemmatiser.
- [[entities/dictionary-of-old-english]] — attested spellings, online through Le.
- [[entities/dictionary-of-old-english-corpus]] — the unlemmatized record those entries are written from. Search: [[skills/using-doec]].
- [[entities/ycoe]] — 1.5 million words of parsed prose. Case from the form, not from the governor.
- [[entities/varioe]] — manual lemmas for that prose, about 30,000, variants often merged.
- [[entities/paveda]] — the government sample.
- [[references/adams-2007-oe-verb-analyzer]] — the finite-state alternative, verbs only.

## Contradictions and Open Questions

- **Two Universal Dependencies “Old Englishes.”** The official UD page publishes only the 20 Cairo sentences and says they are modern sentences translated into Old English, so they are not evidence of historical syntax. The instrumental and the dual are listed as possible and unattested there. Nerthus’s UD_Old_English-OEDT is a separate treebank. The GitHub readme (checked 9 October 2026) describes about 50,000 words: half a revision of Domínguez Barragán 2024, half automatic annotation revised by the ParCor team, from Orosius, Mark, Ælfric’s Catholic Homilies I, Chronicle A, and the Laws. An earlier Hugging Face card stated 55,000 words. It is not the live UD release. ^[ambiguous]
- **Dictionary size.** The 2025 survey, citing Ellis, gives Bosworth about 26,000 entries, Sweet about 12,000, and Clark Hall about 35,000. Tichý’s generator table has 70,914 lemmas, which counts more than one row per word (participles are broken out). Nerthus v5 has 32,812 files. These are different objects. The 26,000 figure should not be used as the size of the online Bosworth–Toller.
- **How many dialects to generate.** Classroom and Wright use West Saxon, Kentish, Mercian, and Northumbrian, with Anglian as the cover of the last two ([[concepts/old-english-dialects]]). Simon den Hertog, *Amsterdamer Beiträge zur älteren Germanistik* 84, no. 4 (2024), argues from historical glottometry for two blocs, Anglian and Saxo-Kentish, and calls the four-way split partly prescriptive. ^[ambiguous] The grammars still write rules at the finer grain. A generator can emit the finer labels and record the coarser grouping as a doubt.
- **95 percent VARIOE accuracy** is stated in Martín Arista’s encyclopedia, not in the frequency-dictionary preface read for this note. The preface does confirm manual lemmatisation and the merging of variants.
- **No one has published** a government entry for every verb and preposition, a dialect-labeled full paradigm, or a segmenter that inflects unseen compounds from the head’s class. Those three are the open build. Tichý’s own test already shows where a West Saxon generator fails: early Kentish prose and Northumbrian glosses, then poetry.

## Sources Consulted

- [[references/tichy-2017-morphological-analyser]] — the generator this repository ported.
- [[references/adams-2007-oe-verb-analyzer]] — finite-state verbs. MAOET and Verbix are named there as the other pre-2017 attempts.
- [[references/nerthus-v5-database]] — class, derivation, attested and generated forms.
- [[references/martin-arista-2026-oe-lemmatisation]] — neural lemmatiser and its error types.
- [[references/ycoe-case-and-pos-annotation]] — why the treebank will not supply government.
- [[references/paveda-old-english-valency]] — the frame sample.
- [[references/computational-study-of-old-english-2025]] — the map of corpora, DOE, VARIOE, and the poetry lemma residue.
- [[references/miani-2025-oe-poetry-pos]] — poetry versus prose tagging.
- [[entities/varioe]] — primary preface of the frequency dictionary, beside the survey’s accuracy claim.

## Sources

- [Tichý 2017](https://casopispromodernifilologii.ff.cuni.cz/wp-content/uploads/sites/9/2017/06/Ondřej_Tichý_40-54.pdf)
- [Nerthus v5](https://www.nerthusproject.com/database-description)
- [Old English lemmatiser](https://huggingface.co/Nerthus-Project/Old_English_Lemmatiser)
- [YCOE POS manual](https://www-users.york.ac.uk/~lang18/Documentation/pos-manual-oe.htm)
- [PaVeDa Old English](https://paveda.unipv.it/contributions/olde1238)
- [Encyclopedia 2025](https://doi.org/10.3390/encyclopedia5030137)
- [ACL 2025 poetry POS](https://aclanthology.org/2025.acl-srw.46.pdf)
