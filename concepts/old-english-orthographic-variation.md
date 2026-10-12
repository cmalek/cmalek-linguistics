---
title: >-
  Old English orthographic variation
category: concepts
tags: [old-english, dialects, orthography]
relationships:
  - target: "[[concepts/old-english-dialects]]"
    type: extends
  - target: "[[references/tichy-2017-morphological-analyser]]"
    type: derived_from
  - target: "[[references/martin-arista-2026-oe-lemmatisation]]"
    type: related_to
sources:
  - "url:https://casopispromodernifilologii.ff.cuni.cz/wp-content/uploads/sites/9/2017/06/Ondřej_Tichý_40-54.pdf"
  - "url:https://doi.org/10.3390/encyclopedia5030137"
  - "url:https://huggingface.co/Nerthus-Project/Old_English_Lemmatiser"
  - "url:https://brill.com/view/journals/abag/84/4/article-p470_2.xml"
  - "url:http://ifa.amu.edu.pl/sap/files/44/08_Adamczyk.pdf"
summary: >-
  Dialect spelling is handled as match-time filters or attested lists. No published generator labels a full paradigm by dialect.
provenance:
  extracted: 0.70
  inferred: 0.22
  ambiguous: 0.08
base_confidence: 0.72
lifecycle: draft
lifecycle_changed: 2026-10-09
tier: supporting
created: 2026-10-09T19:50:00Z
updated: 2026-10-09T19:50:00Z
---

# Old English orthographic variation

Manuscript spelling mixes dialect, date, scriptorium, and scribal habit. A generator has to decide which of those differences are cells it will emit, and whether each cell carries a dialect label.

## What generation projects chose

[[references/tichy-2017-morphological-analyser|Tichý (2017)]] generates one pragmatic paradigm. Differences smaller than the noise in the texts are collapsed. He gives the signal-to-noise example of *-on* versus *-an* when the texts do not respect the textbook distribution. Thorn and eth are one grapheme for matching. Vowel length is stored, and ignored when matching authentic manuscripts, because macrons are editorial.

He then adds **variation filters** at analysis time: character substitutions and regular expressions (back vowels before nasals among them), taken from Baker (2012) and Wright and Wright (1914). The user can enable a subset “given the age and dialect of the text.” He states the reason for not generating every dialectal and diachronic variant up front: the form dictionary would grow by orders of magnitude and become impractical. Filters recover part of the loss. On his sample, overall recall moves from 95 to 97.3 percent. The Kentish charter moves from 84.7 to 94.2. The Northumbrian Lindisfarne gloss only moves from 89.6 to 90.7. Late West Saxon prose was already near 100 percent without filters, which matches a grammar and a dictionary aimed at that variety.

[[references/nerthus-v5-database|Nerthus]] stores alternative spellings on the headword (*āblynnan, onblinnan* beside *āblinnan*) and, in v5, generated forms that the DOEC attests. That is an attested-variant list, not a dialect tag on every unattested cell.

The [[entities/dictionary-of-old-english|DOE]] FORM line is the same kind of object: every spelling the corpus has, sometimes with a note of region, genre, or author. [[references/computational-study-of-old-english-2025|Martín Arista (2025)]] says West Saxon is about 60 percent of what survives, so both the attested lists and any model trained on them lean West Saxon.

## Neural models

[[references/martin-arista-2026-oe-lemmatisation|The 2026 lemmatiser]] augments training by swapping *þ*/*ð*, *æ*/*a*/*e*, and *i*/*y*. About 20 percent of its errors are still spelling variation. The swaps are not labelled West Saxon, Mercian, Northumbrian, or Kentish.

## Dialect labels versus a four-way paradigm

[[concepts/old-english-dialects]] records the classroom map: West Saxon, Kentish, and Anglian (Mercian and Northumbrian), with Wright’s spelling cues (*ea* ~ Anglian *æ*/*e*, Kentish *e* for WS *æ*, and so on). Those cues are the raw material of a variant layer.

Simon den Hertog, “Subgrouping the Old English Dialects Using Historical Glottometry,” *Amsterdamer Beiträge zur älteren Germanistik* 84, no. 4 (2024), treats Anglian as one bloc and West Saxon with Kentish as another (“Saxo-Kentish”), and treats the four-way split as partly prescriptive. ^[ambiguous] That argument does not supply paradigms. The grain the handbooks actually write rules for is a late West Saxon canonical form, then named correspondences for Anglian and Kentish, with Mercian and Northumbrian split only where the endings or the vowels actually differ. ^[inferred] Elżbieta Adamczyk, “Disintegration of the Nominal Inflection in Anglian: The Case of i-Stems,” *Studia Anglica Posnaniensia* 44 (2008), documents one such ending difference: Anglian i-stems take the productive *-as* plural beside the inherited ending, and she lists loss of final *-n* in weak nouns among the Anglian inflectional features.

Inflectional endings differ by dialect as well as stems. Generating “the same endings, different vowels” under-generates Anglian nouns. ^[inferred]

## Related

- [[concepts/old-english-dialects]]
- [[concepts/old-english-form-generation]]
- [[synthesis/danelaw-x-old-english-dialects]]

## Sources

- [[references/tichy-2017-morphological-analyser]]
- [[references/nerthus-v5-database]]
- [[references/martin-arista-2026-oe-lemmatisation]]
- [[references/computational-study-of-old-english-2025]]
