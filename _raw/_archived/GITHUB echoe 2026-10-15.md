---
title: "echoe"
owner: "ECHOEProject"
source: "https://github.com/ECHOEProject/echoe"
website:
description: "Electronic Corpus of Anonymous Homilies in Old English"
stars: "4"
language: "\"TeX89.3%, XSLT8.7%, CSS1.3%, Python0.7%\""
tags:
  - "old_english"
  - "prose"
  - "text"
created: 2026-10-15
---
## README

Electronic Corpus of Anonymous Homilies in Old English

## About

ECHOE is a text corpus encoding all extant witnesses to anonymous and Wulfstanian Old English homiletic and long-format hagiographical prose predating c. 1200 in TEI P5 XML. It forms the basis of [ECHOE Online](https://echoe.uni-goettingen.de). Consult the [documentation](/ECHOEProject/echoe/blob/main/doc/documentation.pdf) for a detailed account of the corpus and the underlying design principles.

## Repository Structure   
| Folder      | Description                                                                 |
| ----------- | --------------------------------------------------------------------------- |
| `doc`       | [Corpus documentation](/ECHOEProject/echoe/blob/main/doc/documentation.pdf) |
| `ebook`     | EPUB release                                                                |
| `metadata`  | Selected metadata extracted from or supplementing the corpus                |
| `misc`      | Schema files; Python scripts; sample stylesheets; bibliography              |
| `plaintext` | A plaintext rendering of the corpus                                         |
| `xml`       | XML corpus                                                                  |

The plaintext and ebook corpora, included as a courtesy to the user, represent a normalized transformation that accepts the most recent scribal revision as well as all editorial emendations. The scripts and stylesheets included in `misc/` may be consulted or adapted for the purpose of custom transformation. The CSS is declared in the XML documents to enable local in-browser reading.

## Contact

You may submit bug reports using GitHub's [issue tracker](https://github.com/ECHOEProject/echoe/issues), or contact [Paul Langeslag](mailto:planges@uni-goettingen.de) on technical matters. For strategic inquiries please get in touch with [Winfried Rudolf](mailto:winfried.rudolf@phil.uni-goettingen.de).

