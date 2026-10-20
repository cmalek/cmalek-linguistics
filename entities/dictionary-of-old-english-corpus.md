---
title: >-
  Dictionary of Old English Corpus
category: entities
tags: [old-english, corpus, lexicography]
relationships:
  - target: "[[entities/dictionary-of-old-english]]"
    type: related_to
  - target: "[[skills/using-doec]]"
    type: related_to
  - target: "[[references/doec-2009-release]]"
    type: related_to
  - target: "[[entities/ycoe]]"
    type: related_to
  - target: "[[concepts/old-english-orthographic-variation]]"
    type: related_to
  - target: "[[concepts/old-english-form-generation]]"
    type: related_to
sources:
  - "url:https://indiv.corpus.doe.utoronto.ca/doecorpus/#/lot/cats/oe/groups/idxcn/indexes/F"
  - "url:https://indiv.corpus.doe.utoronto.ca/doecorpus/#/lot/cats/oe/groups/idxcn/indexes/E"
  - "url:https://indiv.corpus.doe.utoronto.ca/doecorpus/#/lot/cats/oe/groups/idxcn/indexes/D"
  - "url:https://indiv.corpus.doe.utoronto.ca/doecorpus/#/lot/cats/oe/groups/idxcn/indexes/C"
  - "url:https://indiv.corpus.doe.utoronto.ca/doecorpus/#/lot/cats/oe/groups/idxcn/indexes/B"
  - "url:https://indiv.corpus.doe.utoronto.ca/doecorpus/#/lot/cats/oe/groups/idxcn/indexes/A"
  - "url:https://doe.artsci.utoronto.ca/?p=197"
  - "url:https://doe.artsci.utoronto.ca/?p=195"
  - "url:https://doe.artsci.utoronto.ca/?p=498"
  - "url:https://doe.artsci.utoronto.ca/?p=990"
  - "url:https://doe.artsci.utoronto.ca/?p=1160"
  - "url:https://doe.artsci.utoronto.ca/?page_id=11"
  - "url:https://varieng.helsinki.fi/CoRD/corpora/DOEC/"
  - "url:https://varieng.helsinki.fi/CoRD/corpora/DOEC/basic.html"
  - "url:http://www.old-engli.sh/documents/news%20documents/DOE_report_2019.pdf"
summary: >-
  Toronto corpus of surviving Old English. The 2009 release has 3,060 texts; the Web Corpus is the subscribed search.
provenance:
  extracted: 0.95
  inferred: 0.05
  ambiguous: 0
base_confidence: 0.74
lifecycle: draft
lifecycle_changed: 2026-10-12
tier: supporting
created: 2026-10-12T04:37:00Z
updated: "2026-10-18T19:48:28.152600+00:00"
snapshots:
  - "[[_raw/_archived/Old English Corpus Cameron A*|Old English Corpus Cameron A*]]"
  - "[[_raw/_archived/Old English Corpus Cameron B*|Old English Corpus Cameron B*]]"
  - "[[_raw/_archived/Old English Corpus Cameron C*|Old English Corpus Cameron C*]]"
  - "[[_raw/_archived/Old English Corpus Cameron D*|Old English Corpus Cameron D*]]"
  - "[[_raw/_archived/Old English Corpus Cameron E*|Old English Corpus Cameron E*]]"
  - "[[_raw/_archived/Old English Corpus Cameron F*|Old English Corpus Cameron F*]]"
---

# Dictionary of Old English Corpus

The Dictionary of Old English Corpus (DOEC) is the textual database of the [[entities/dictionary-of-old-english|Dictionary of Old English]] at the University of Toronto. The dictionary’s About page states the method in one line: the corpus, not an earlier dictionary, determines the headwords, the definitions, and the quotations. The project describes it as at least one copy of every surviving Old English text. The 2009 release page adds the limit: some variant manuscripts of individual texts are left out. Helsinki CoRD, in an entry submitted by Antonette diPaolo Healey, adds the other half of that rule: a second copy is included when dialect or date makes it worth having.

The corpus was built for the dictionary’s own editors and then distributed to other scholars. The first release was 1981. The Web Corpus opened to institutions in 1997 and to individual subscribers in 2007. The November 2009 release is the last one with a published text count and a published word count. A later Web Corpus, announced after the 2024 La–Le fascicle, carries corrections since 2009, newer editions (especially charters), and a new search address. That announcement does not print a new total. Counts below are the 2009 release unless a later report is named.

Search steps are on [[skills/using-doec]]. The 2009 file layout and the Cameron prefixes are on [[references/doec-2009-release]].

## What a record is

A corpus file is an edition, cut into citations. It is not a lemma list and it is not a parsed treebank. Peter A. Stokes, *Florilegium* 26 (2009), says the text was still not lemmatized. The 2009 release agrees in what it encodes. Each text is a TEI document. The `xml:id` is `T` plus a text number (`T00010`). The `teiHeader` holds the title, the bibliography, and the encoding description. Each citation is an `s` element. Its attributes carry a citation number and a text-reference identifier, and the shape of that identifier changes from text to text. The header says which system that text uses.

Latin or Greek inside an Old English text, and Latin that Old English glosses, sits in `foreign`. A word that is fragmentary in the manuscript, or emended by the editor, sits in `corr`. The same tag can mark a problem in the manuscript beside the word. Runic text sits in `hi` with `rend="rune"`. In the HTML view the same facts are italics, angle brackets, and `//`. Editorial punctuation is usually the editor’s, and for most texts it follows modern norms. The HTML header also stores a Short Title, a shorter short title, and the Cameron number.

Cameron numbers are the catalogue. The 2009 release points at Angus Cameron, “A List of Old English Texts,” in Roberta Frank and Angus Cameron, eds., *A Plan for the Dictionary of Old English* (Toronto: University of Toronto Press, 1973), 25–306. Each file’s bibliography is the updated Healey–Venezky list. The letter prefix is the class:

| Prefix | Class |
|---|---|
| A | Poetry |
| B | Prose |
| C | Interlinear glosses |
| D | Glossaries |
| E | Runic inscriptions |
| F | Inscriptions in the Latin alphabet |

Stokes notes that the number under the letter still sorts the material: `A1` is the poetry of the Junius manuscript, so a Cameron limit can select a manuscript as well as a genre. The Web Corpus also searches by the project’s short titles. The teaching video uses `Beo` for *Beowulf*.

## 2009 size

CoRD’s table for the 2009 release, in the entry Healey submitted:

| Category | Old English words | Foreign words |
|---|---:|---:|
| A Poetry | 177,480 | 255 |
| B Prose | 2,128,781 | 52,038 |
| C Interlinear glosses | 699,606 | 635,655 |
| D Glossaries | 26,598 | 70,511 |
| E Runic inscriptions | 346 | 4 |
| F Inscriptions in the Latin alphabet | 331 | 40 |
| Total | 3,033,142 | 758,503 |

There are 3,060 texts. The XML file is about 62 megabytes and follows TEI P5 (Sperberg-McQueen and Burnard, 2008). CoRD’s summary line says “ca. 3 million running words of Old English, ca. 1 million running words of Latin.” The table’s foreign-word total is 758,503. Those are the two figures the project-side descriptions print. The About page’s comparison is “almost five times the collected works of Shakespeare.” The period CoRD gives is about 600–1150.

Prose is most of the Old English. Glosses are where the Latin sits: interlinear glosses have almost as many foreign words as Old English words, and glossaries have more foreign words than Old English words. Poetry is 177,480 Old English words. Inscriptions are a few hundred words each. That poetry block is the part a prose-only corpus such as ParCorOEv3 does not have.

## The Web Corpus after 2009

The 2019 progress report (Getz and Pelle) describes the revision then underway. Catherine Monahan was replacing charter texts drawn from Kemble and Birch with the British Academy Anglo-Saxon Charters series. About a dozen newly found charters had been added, most of them from Simon Keynes’s work on a modern transcript of a lost St Albans cartulary. The report says those texts enlarged the corpus by several thousand words and supplied lexical items no dictionary had recorded, including *ealdorcyre* ‘suitable choice for a superior’ and *geondra* ‘farther, more distant’. The report hoped to release that version before DOE: La–Le.

The project’s later announcement says the new Electronic Corpus is that release: improved search, every correction since 2009, and newer editions of many works, especially charters. It does not repeat the 2019 word-count delta, and the 2025 progress report does not discuss the corpus. The public total therefore remains the 2009 table. The CD-ROM page, which still describes the 2009 disc and its 3,060 texts, says that as of 2025 the disc is no longer sold except in special circumstances, and that the disc includes no search engine.

## Who publishes it

The 1981 compilers were Angus Cameron, Ashley Crandell Amos, Sharon Butler, and Antonette diPaolo Healey. The 2009 compilers were Healey, Joan Holland, Ian McDougall, and David McDougall, with Xin Xiang’s TEI-P5 version. Catherine Monahan was copy-editor of that release. The Web Corpus product page names Healey as editor, with John Price Wilkin and Xin Xiang, and gives the site ISBN 0-472-00277-5.

Healey retired in 2014. The 2025 progress report’s editorial staff is Robert Getz and Stephen Pelle (co-editors), Cameron Laird (copy editor), Xi Wang, and Deanna Brooks. Healey sits on the International Advisory Committee. The office is Robarts Library, room 14285, 130 St. George Street, Toronto. The 2025 report’s letterhead prints 416-978-8883. A capture of the contact page prints 416-978-0201. The fax on both is 416-978-8835.

The 2009 release was supported in part by the Social Sciences and Humanities Research Council of Canada and the National Endowment for the Humanities. CoRD also lists the British Academy, the Gladys Krieble Delmas Foundation, the Jackman Foundation, the McLean Foundation, the Andrew W. Mellon Foundation, the Salamander Foundation, the St. George’s Society, the Triangle Community Foundation, and the University of Toronto.

## What a generator can take from it

- **An attested spelling in a named text.** A hit is a citation, a Cameron number, and a short title. That is the inventory [[references/tichy-2017-morphological-analyser|Tichý]] intersected with generation when he dropped unattested cells. It is also the inventory that still contains a poetic compound ParCor never saw.
- **A second copy when the project judged dialect or date worth keeping.** Those extra manuscripts are in the files. The corpus does not label the citation West Saxon, Mercian, Northumbrian, or Kentish.
- **The quotation behind a published dictionary entry.** Where [[entities/dictionary-of-old-english|DOE]] has reached (A to Le online), the entry’s form list and citations are the analyzed view of this same evidence.

## What it does not store

The distributed text has no lemma, no stem class, and no case frame. A wildcard such as `*helm*` in the teaching video finds the string inside inflected forms and compounds. It does not parse them. [[entities/ycoe|YCOE]] is a parsed prose sample with its own tagset. It is not this corpus. Government of case is not a DOEC field. See [[concepts/old-english-case-government]] and [[entities/paveda|PaVeDa]].

The 2009 release is explicit about reuse. The scholar clears copyright with the editors and publishers of the editions being cited. The Dictionary of Old English holds copyright in the compilation and its tagging. The corpus is not to be copied or redistributed without written consent. It is not to be placed on the open Internet. An institutional web server limited to that institution’s users is the exception the release page allows. A morphology project can search the corpus. It cannot ship the files.

## How to open it

The Web Corpus is the search. The product page lists institutions at $200 a year (trial access on request) and individuals at $75 a year, with 20 free logins a year before an invoice. Outside Canada the prices are in US dollars. Store accounts are created at the DOE online store.

Doors named on the project site:

- Institutional, on campus, from the new-corpus announcement: https://corpus.doe.utoronto.ca
- Institutional path printed on the contact page: https://corpus.doe.utoronto.ca/doecorpus/#/oec
- Individual subscribers: https://indiv.corpus.doe.utoronto.ca/

Off-campus institutional users are told to use the library catalogue link, because a proxy may still point at the old address. The individual door asks for the subscription email and the usual corpus password, and the announcement says the password is entered twice before the corpus displays. The procedure once inside is [[skills/using-doec]].

During the outage that preceded this release, the La–Le announcement pointed at an older, searchless copy at the Oxford Text Archive, with the conditions in that copy’s `corpus.htm`. That note was a temporary bridge. The current door is the Web Corpus above.

Cite the 2009 release as CoRD gives it: *Dictionary of Old English Corpus*, original release (1981) compiled by Angus Cameron, Ashley Crandell Amos, Sharon Butler, and Antonette diPaolo Healey (Toronto: DOE Project, 1981); 2009 release compiled by Antonette diPaolo Healey, Joan Holland, Ian McDougall, and David McDougall, with TEI-P5 version by Xin Xiang (Toronto: DOE Project, 2009).

## Related

- [[entities/nerthus-project]]
- [[entities/bosworth-toller]]
- [[synthesis/Research: Old English Morphology Generation]]

## Local catalogue snapshots

[[references/doec-cameron-catalogue]] provides a local map of all six captured catalogue divisions. Preserve the record’s citation convention when following a result: corpus identifiers do not imply one universal page or line numbering system.

## Sources

- [2009 release](https://doe.artsci.utoronto.ca/?p=197) (text read from the Internet Archive capture; the live host returned a browser check)
- [Corpus on CD-ROM](https://doe.artsci.utoronto.ca/?p=195)
- [Web Corpus subscription](https://doe.artsci.utoronto.ca/?p=498)
- [New Electronic Corpus](https://doe.artsci.utoronto.ca/?p=990)
- [Individual-subscriber door](https://doe.artsci.utoronto.ca/?p=1160)
- [About the DOE](https://doe.artsci.utoronto.ca/?page_id=11)
- [CoRD: DOEC](https://varieng.helsinki.fi/CoRD/corpora/DOEC/)
- [CoRD: 2009 word counts](https://varieng.helsinki.fi/CoRD/corpora/DOEC/basic.html)
- [2019 progress report](http://www.old-engli.sh/documents/news%20documents/DOE_report_2019.pdf)
- Peter A. Stokes, “The Digital Dictionary,” *Florilegium* 26 (2009): 37–69
- [[_raw/_archived/Old English Corpus Cameron A*.md]]
- [[_raw/_archived/Old English Corpus Cameron B*.md]]
- [[_raw/_archived/Old English Corpus Cameron C*.md]]
- [[_raw/_archived/Old English Corpus Cameron D*.md]]
- [[_raw/_archived/Old English Corpus Cameron E*.md]]
- [[_raw/_archived/Old English Corpus Cameron F*.md]]
