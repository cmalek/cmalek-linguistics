---
title: >-
  Using the DOEC
category: skills
tags: [old-english, corpus, workflow]
relationships:
  - target: "[[entities/dictionary-of-old-english-corpus]]"
    type: uses
  - target: "[[references/doec-2009-release]]"
    type: uses
  - target: "[[entities/dictionary-of-old-english]]"
    type: related_to
  - target: "[[concepts/old-english-orthographic-variation]]"
    type: related_to
sources:
  - "url:https://doe.artsci.utoronto.ca/?p=498"
  - "url:https://doe.artsci.utoronto.ca/?p=990"
  - "url:https://doe.artsci.utoronto.ca/?p=1160"
  - "url:https://doe.artsci.utoronto.ca/?page_id=382"
  - "url:https://doe-omeka.library.utoronto.ca/items/show/35"
  - "url:https://doe-omeka.library.utoronto.ca/items/show/36"
  - "url:https://doe-omeka.library.utoronto.ca/items/show/38"
summary: >-
  How to open the DOE Web Corpus and search a spelling, a text, or a phrase. Hits are attestations, not lemmas.
provenance:
  extracted: 0.84
  inferred: 0.10
  ambiguous: 0.06
base_confidence: 0.70
lifecycle: draft
lifecycle_changed: 2026-10-12
tier: supporting
created: 2026-10-12T04:37:00Z
updated: 2026-10-12T04:37:00Z
---

# Using the DOEC

The Dictionary of Old English Web Corpus is a subscription search over the [[entities/dictionary-of-old-english-corpus|DOEC]]. The 2009 CD-ROM has the texts and no search engine, and as of 2025 it is not normally sold. Background and the 2009 counts are on the corpus page.

The project’s 2014 help manual and its two corpus videos (Alexandra Bolintineanu, Xin Xiang, and Antonette diPaolo Healey, on the Toronto “A Word Is Born” site) describe the search gestures below. The new-corpus announcement says the current site has improved search and does not print a new operator list. Treat the 2014 gestures as the last written manual, and expect the screen to have moved.

## Key Ideas

**Open the right door.** Institutions, on campus: https://corpus.doe.utoronto.ca. The contact page also prints https://corpus.doe.utoronto.ca/doecorpus/#/oec. Off campus, use the library catalogue so the proxy is updated. Individuals: https://indiv.corpus.doe.utoronto.ca/, subscription email, then the usual corpus password. The individual announcement says the password is entered a second time before the corpus displays. The product page lists institutions at $200 a year and individuals at $75 a year, with 20 free logins a year from a store account before an invoice. Outside Canada the prices are US dollars.

**Search one spelling.** Type the string and press Search. Restrict by class (the video’s example is verse) or by short title. Short titles and Cameron numbers are on List of Texts: *Beowulf* is `Beo`. The citation’s opening link is the full title and the bibliography. In the video, plain `helm` returns 110 citations, 28 of them in *Beowulf*.

**Include inflections and compounds with asterisks.** The same video puts asterisks around `helm` and, still inside *Beowulf*, goes from 28 citations to 43. The extra hits are strings that contain `helm`, such as *helme* and *grimhelmas*. That is a character search. The corpus is not lemmatized, so the asterisk is how a paradigm cell or a compound is found. `?` in a slashed expression is one character. `*` is empty, one character, or many.

**Search a phrase.** Two words, or the first word plus AND, returns citations that contain both, in either order. The video’s pair is `hus` and `ham`, seven citations. Order is a slashed expression: `/hus * ham/` keeps only that order and allows anything between the words, four citations in the video. Leave out the `*` between the slashes and the slashes are stripped, which falls back to the unordered search. Proximity is a second step: run the two words with no slashes and no asterisks, then set Proximity Distance under the spelling combinations.

**Read a hit as an attestation.** You get the citation, the short title or Cameron number, and the edition’s spelling, including a poetic spelling ParCor will not have. You do not get stem class, a dialect label, or a filled paradigm. For class on a headword the dictionary already publishes, use [[entities/dictionary-of-old-english]]. For a word past Le, the corpus hit is evidence that the string occurs. The class still has to come from somewhere else.

**Stay inside the licence.** The 2009 release forbids redistribution and forbids putting the files on the open Internet. An institutional server limited to that institution’s users is the exception it names. Citing a passage still means clearing the edition’s own copyright. The compilation and its tagging are the Dictionary of Old English’s.

## Open Questions

- Whether the 2025 search screen still uses the 2014 asterisk, slash, and proximity controls. The announcement says the search was improved and does not restate the operators.
- The word count of the post-2009 Web Corpus. The announcement describes corrections and newer charter editions and does not print a new total.

## Sources

- [Web Corpus subscription](https://doe.artsci.utoronto.ca/?p=498)
- [New Electronic Corpus](https://doe.artsci.utoronto.ca/?p=990)
- [Individual door](https://doe.artsci.utoronto.ca/?p=1160)
- [Basic search video](https://doe-omeka.library.utoronto.ca/items/show/35)
- [Phrase search video](https://doe-omeka.library.utoronto.ca/items/show/36)
- [Help manual, 21 July 2014](https://doe-omeka.library.utoronto.ca/items/show/38)
