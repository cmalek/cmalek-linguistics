---
title: >-
  DOEC 2009 release
category: references
tags: [old-english, corpus, tei]
sources:
  - "url:https://doe.artsci.utoronto.ca/?p=197"
  - "url:https://varieng.helsinki.fi/CoRD/corpora/DOEC/"
  - "url:https://varieng.helsinki.fi/CoRD/corpora/DOEC/basic.html"
source_url: "https://doe.artsci.utoronto.ca/?p=197"
relationships:
  - target: "[[entities/dictionary-of-old-english-corpus]]"
    type: related_to
  - target: "[[skills/using-doec]]"
    type: related_to
summary: >-
  November 2009 DOEC: 3,060 texts, TEI-P5 and HTML, Cameron prefixes, and the published word counts.
provenance:
  extracted: 0.88
  inferred: 0.08
  ambiguous: 0.04
base_confidence: 0.72
lifecycle: draft
lifecycle_changed: 2026-10-12
tier: supporting
created: 2026-10-12T04:37:00Z
updated: 2026-10-12T04:37:00Z
---

# DOEC 2009 release

[The Dictionary of Old English Corpus in Electronic Form, 2009 release](https://doe.artsci.utoronto.ca/?p=197), November 2009, Dictionary of Old English Project, University of Toronto. The live host returned a browser check during this research. The text below is the Internet Archive capture of that page, checked against the CoRD entry Antonette diPaolo Healey submitted on 23 November 2009.

The page calls the corpus a complete record of surviving Old English except for some variant manuscripts of individual texts. There are **3,060 texts**, in TEI-P5 XML (about 62 megabytes) and in HTML. Compilers of this release, as CoRD states them: Antonette diPaolo Healey, Joan Holland, Ian McDougall, and David McDougall, with the TEI-P5 version by Xin Xiang. Copy-editor Catherine Monahan. The 1981 release was Cameron, Ashley Crandell Amos, Sharon Butler, and Healey.

## What the disc contains

`corpus.html` is the HTML index by short title. `html/st2cn.html` and `html/cn2st.html` convert short title and Cameron number. `html/wordcount.html` is the per-text word count. `xml-corpus/corpus.xml` is the XML control file, `textlist.xml` the text list, `corpus.ent` the character entities that have no standard XML match.

Each HTML text file’s header holds the short title, the shorter short title, the Cameron number, and the bibliography (the updated Healey–Venezky list). Each citation begins with a citation number and a text-reference identifier. In the XML, each text is a `TEI` element whose `xml:id` is `T` plus the text number. Citations are `s` elements. The text-reference identifier is the `n` attribute, and `encodingDesc` says which reference system that text uses.

Latin and Greek, and Latin glossed by Old English, are `foreign` (italics in HTML). Fragmentary or emended words are `corr` (angle brackets in HTML). The release page says that tag can also mark a manuscript problem beside the word. Runic text is `hi rend="rune"` (`//` in HTML).

Cameron prefixes on the release page: **A** poetry, **B** prose, **C** interlinear glosses, **D** glossaries, **E** runic inscriptions, **F** inscriptions in the Latin alphabet. The catalogue is Cameron’s “A List of Old English Texts” in Frank and Cameron, *A Plan for the Dictionary of Old English* (1973), 25–306.

## Word counts

CoRD prints this table for the 2009 release. The same entry’s summary line says about 3 million running words of Old English and about 1 million of Latin. The table’s foreign total is 758,503.

| Category | Old English | Foreign |
|---|---:|---:|
| A Poetry | 177,480 | 255 |
| B Prose | 2,128,781 | 52,038 |
| C Interlinear glosses | 699,606 | 635,655 |
| D Glossaries | 26,598 | 70,511 |
| E Runic inscriptions | 346 | 4 |
| F Latin-alphabet inscriptions | 331 | 40 |
| Total | 3,033,142 | 758,503 |

## Distribution

Academic copies were US$200 including shipping, HTML and XML, with no search engine on the disc. The Web Corpus was already the subscribed search. The later CD-ROM page says that as of 2025 the disc is no longer sold except in special circumstances. Reuse on the 2009 page: the user clears the edition’s copyright; the corpus is not redistributed without the project’s written consent; it is not placed on the open Internet; an institutional server limited to that institution’s users is allowed. CoRD adds that the DOE owns copyright in the compilation and its tagging.

The later Web Corpus is a different release. See [[entities/dictionary-of-old-english-corpus]].

## Sources

- [2009 release notes](https://doe.artsci.utoronto.ca/?p=197)
- [CoRD entry](https://varieng.helsinki.fi/CoRD/corpora/DOEC/)
- [CoRD word counts](https://varieng.helsinki.fi/CoRD/corpora/DOEC/basic.html)
