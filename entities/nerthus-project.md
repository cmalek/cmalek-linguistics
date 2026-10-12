---
title: >-
  Nerthus Project
category: entities
tags: [old-english, lexicography, corpus, project]
relationships:
  - target: "[[references/nerthus-v5-database]]"
    type: related_to
  - target: "[[skills/using-nerthus]]"
    type: related_to
  - target: "[[entities/javier-martin-arista]]"
    type: related_to
  - target: "[[entities/paveda]]"
    type: related_to
  - target: "[[concepts/old-english-inflectional-class]]"
    type: implements
  - target: "[[concepts/oe-word-formation]]"
    type: implements
sources:
  - "url:https://www.nerthusproject.com/"
  - "url:https://www.nerthusproject.com/about-us"
  - "url:https://www.nerthusproject.com/previous-versions-1"
  - "url:https://www.nerthusproject.com/database-description"
  - "url:https://www.nerthusproject.com/search-nerthusv5"
  - "url:https://www.nerthusproject.com/corpus-description"
  - "url:https://www.nerthusproject.com/corpus-methodology"
  - "url:https://www.nerthusproject.com/previous-versions"
  - "url:https://www.nerthusproject.com/how-to-cite-2"
  - "url:https://www.nerthusproject.com/how-to-cite"
  - "url:https://varieng.helsinki.fi/CoRD/corpora/Nerthus/structure.html"
  - "url:https://github.com/dmetola/Old_English-OEDT"
summary: >-
  La Rioja knowledge base of Old English: Nerthus v5 (32,812 headwords), ParCorOEv3 prose, and a guest WebDirect search.
provenance:
  extracted: 0.82
  inferred: 0.12
  ambiguous: 0.06
base_confidence: 0.74
lifecycle: draft
lifecycle_changed: 2026-10-09
tier: supporting
created: 2026-10-09T19:50:00Z
updated: 2026-10-09T20:32:00Z
---

# Nerthus Project

The Nerthus Project at the University of La Rioja compiles a knowledge base of Old English and publishes it as open-access databases. The public aim, on the project home page, is to join a philological tradition to corpus linguistics and computational parsing. The working object is a set of relational databases the project calls the Knowledge Base of Old English. [[entities/javier-martin-arista|Javier Martín Arista]] directs it. The public site is [nerthusproject.com](https://www.nerthusproject.com/). Contact is javier.martin@unirioja.es.

Two databases are the ones a morphology generator can open today. **Nerthus v5** (2024) is the lexicon: 32,812 headword files, with inflectional class, derivation, dictionary meanings, and attested forms. **ParCorOEv3** (2023) is a prose parallel corpus of Old English and Present-Day English, 303,342 records. A third public object, the Universal Dependencies treebank on GitHub, is a ~50,000-word conversion of five of those prose texts. It is a treebank, and the lexicon stays in FileMaker. Search steps are on [[skills/using-nerthus]]. The field inventory is on [[references/nerthus-v5-database]].

## Version history

The project’s own version page gives this sequence.

- **Nerthus v2 (2009).** Editors Martín Arista, Caballero González, González Torres, Ibáñez Moreno, and Torre Alonso. Word-formation: affixation, compounding, and zero derivation. From v2 the database is searchable and open access.
- **Nerthus v3 (2016).** Editors Martín Arista, García Fernández, Lacalle Palacios, Ojanguren López, and Ruiz Narbona. A paradigmatic analysis, including processes the project calls formally transparent and formally opaque. Helsinki CoRD documents this file: 31,298 entries. Class labels came from Clark Hall, Bosworth–Toller (Toller’s supplement and Campbell’s addenda), and Sweet. The DOE was not a class source. Strong-verb subclasses follow Krygier (1994). Comparison follows Seelig (1930). The sample row is *āblinnan* / *āblynnan*, *onblinnan*, strong III. Hypothetical predicates are 65 files, and a hypothetical is allowed only when the source, the target, and the process are each attested elsewhere.
- **v4** was not published. The project describes it as a transition into v5.
- **Nerthus v5 (2024).** Citation below. New in this version, in the project’s words: a dictionary interface that compares current Old English dictionaries; attested inflectional forms from morphological generation for all inflecting classes; references to the headword in secondary sources; and a ParCorOEv3 citation for every headword that occurs in the corpus.

CoRD’s 2016 door is `https://fm1.apps.unirioja.es/fmi/webd#Nerthusv3` (FileMaker Pro 14). The doors linked from the site in 2026 are the v5 and ParCor WebDirect URLs under How to open it.

## What Nerthus v5 holds

Headword spelling follows Clark Hall. Each file has three headword shapes: a simplex that ignores *ge-*, an alphabetical headword, and a numbered headword that splits homographs and alternative spellings. Meaning comes from Sweet, Clark Hall, and [[entities/bosworth-toller|Bosworth–Toller]], plus a synthetic definition. [[entities/dictionary-of-old-english|DOE]] headwords are linked for A–I.

Part of speech on the headword is lexical category and inflectional class together. That pair is what a generator copies. A Universal Dependencies UPOS tag does not carry the class.

Inflection is four lists: forms printed in Bosworth–Toller, forms from secondary sources, forms in ParCorOEv3, and automatically generated canonical forms that are attested in the DOEC. The generated list is an attested subset. Unattested grammatical cells are outside it, the same design [[references/tichy-2017-morphological-analyser|Tichý]] uses when he intersects generation with the DOEC.

Derivation, for every non-basic word, is one of affixation, zero derivation, affixless derivation, or compounding, with base, category of the base, affix, and a lexical prime. See [[concepts/oe-word-formation]].

Alternative spellings on the headword are dictionary and attested variants. The database does not label each cell as West Saxon, Mercian, Northumbrian, or Kentish.

The references index points at secondary literature discussed for a headword (the project bibliography runs from Anlezark, Baker and Lapidge, Bammesberger, and onward). One ParCor citation, with a Present-Day English translation, is stored for each headword the corpus represents.

## ParCorOEv3

The corpus-description page: 303,342 records, one token each, prose only. The methodology page describes the same release as 300,000 Old English words plus the Present-Day English parallel. The per-text counts on the description page add to 303,342.

| Siglum | Records | Siglum | Records |
|---|---:|---|---:|
| ÆHOM | 37,135 | LEEC | 11,883 |
| OROS | 27,874 | MARK | 12,031 |
| CHAR | 25,887 | HERB | 10,863 |
| ASCE | 25,431 | LACN | 8,901 |
| LAWS | 25,016 | WILL | 7,565 |
| MART | 24,355 | APOL | 6,579 |
| BOET | 23,972 | QUAD | 4,337 |
| BERU | 20,376 | SOLI | 15,535 |
| ASCA | 15,602 | | |

Each record shows the token, a file number, lemma, lexical category, inflectional category, gloss, a concordance (prefield and postfield), a Present-Day English translation of the fragment, and the sources of both texts. Alignment is at text, fragment, sentence, and word. The software is FileMaker, published with WebDirect.

History, from the corpus version page: v1 in 2018 was a 10,000-word pilot (Anglo-Saxon Chronicle, Orosius, Ælfric’s Lives of Saints, Cura Pastoralis, Bede), drawn from Fernández Cuesta et al. (1997). v2 in 2021 was 110,000 words. v3 passed 300,000 words, partly automated the processing, revised proper names, patronymics, and nationality nouns and adjectives, and wired quotations into the dictionary interface. The version page once prints “PacCorOEv3” for this corpus.

The methodology page required the pilot to import lemma, alternative spellings, lexical category, morphological class, inflectional paradigm, derivational paradigm, and meaning from the knowledge base. The 2023 public field list names the token’s morphological tag **inflectional category**. A ParCor token row is evidence of an attested prose form and a lemma. Stem class for generation still comes from the Nerthus headword, where class is an explicit field. ^[ambiguous]

Genre is prose. Poetic hapax compounds are outside this corpus. The GitHub readme says the 303,342 records are about one tenth of the surviving written record, and that later releases of the treebank are planned to cover the whole of ParCor.

## The dependency treebank

[UD_Old_English-OEDT](https://github.com/dmetola/Old_English-OEDT) (Darío Metola; contributors Javier Martín Arista and Darío Metola) is about 50,000 Old English words, 68,689 annotation lines, license CC BY-SA 4.0, listed as available since UD v2.15. Half is a revision of Sara Domínguez Barragán’s 2024 La Rioja dissertation (~25,000 words). Half was annotated automatically and revised by the ParCor team (~25,000). Texts: Orosius, St Mark, Ælfric’s Catholic Homilies I, Anglo-Saxon Chronicle A, and the Laws. Lemmas come from the 2011 Nerthus headword list (Martín Arista et al., *Working Papers in Early English Lexicology and Lexicography* 1). Negative contractions with *ne* are `Polarity=Neg` on one token. The readme’s feature example does carry case, gender, and number. The official UD language sample remains a separate 20-sentence Cairo set. An earlier Hugging Face card figure of 55,000 words is a second public number for this treebank family. ^[ambiguous]

## People and support

The 2024 Nerthus v5 citation names the editorial team: Javier Martín Arista (ed.), Sara Domínguez Barragán, Luisa Fidalgo Allo, Laura García Fernández, Yosra Hamdoun Bghiyel, Miguel Lacalle Palacios, Raquel Mateo Mendaza, Carmen Novo Urraca, Ana Elvira Ojanguren López, Esaúl Ruíz Narbona, Roberto Torre Alonso, Marta Tío Sáenz, and Raquel Vea Escarza.

Associate researchers on the about page include Monika Kirner-Ludwig, Ruth Möhlig-Falke, Susan Pintzuk, Hans Sauer, Katarzyna Sówka-Pietraszewska, Ondřej Fúsik (Charles University), Alena Novotná (Charles University), Martina Giarda (University of Pavia; see [[entities/paveda]]), and Matías Núñez. The name Ondřej Fúsik is copied as the page prints it. The current grant named on the GitHub readme and the about page is PID2023-149762NB-100 (MICIU/AEI). The site footer signs the group as RGFGs. CoRD’s 2016 Nerthus page uses the name Functional Grammars Research Group for this department’s corpus work.

## What a generator can take from it

- **Class, for a headword already in the 32,812.** Copy lexical category and inflectional class. Search the simplex when *ge-* is optional. Search the full compound or prefixed headword when that string might be its own entry (*æt-swymman* is the kind of prefixed headword Tichý also kept). A miss means that string is outside this file, so class has to come from the right-hand head. See [[concepts/old-english-inflectional-class]].
- **Attested spellings and attested cells.** The four inflection lists, plus ParCor tokens, are evidence of forms that occur. They are the check on a paradigm, and they are a different layer from a generated late West Saxon cell that the corpus never shows.
- **Derivational status.** The base, the affix, and the process say whether a word is a compound or a prefixed derivative. v3’s 65 hypotheticals are a closed set of predicted derivatives, and they are not an open compound generator.
- **A prose citation.** ParCor supplies a token, a gloss, and a translation when the headword occurs in those seventeen texts.

## What it does not store

Government of case by verbs and prepositions is not a Nerthus field. Frames for the 80 ValPaL meanings are in [[entities/paveda|PaVeDa]]. See [[concepts/old-english-case-government]]. Dialect-labeled full paradigms are not in the inflection lists. The teaching page on the site is course advertising, and it is not a search manual. The project pages describe open-access search through a browser. They do not link a download of the 32,812 files. Guest export rights are not stated on those pages.

## How to open it

Set the browser language to English. Nerthus v5: [https://muga.unirioja.es/fmi/webd/ONLINENerthusV5.fmp12](https://muga.unirioja.es/fmi/webd/ONLINENerthusV5.fmp12). ParCor: [https://muga.unirioja.es/fmi/webd/ONLINEParcor.fmp12](https://muga.unirioja.es/fmi/webd/ONLINEParcor.fmp12). Both hosts returned HTTP 200 on 9 October 2026. That check did not complete a guest session. Sign in as Guest, then follow [[skills/using-nerthus]].

Cite Nerthus v5 as the project asks:

> Martín Arista, Javier (ed.), Sara Domínguez Barragán, Luisa Fidalgo Allo, Laura García Fernández, Yosra Hamdoun Bghiyel, Miguel Lacalle Palacios, Raquel Mateo Mendaza, Carmen Novo Urraca, Ana Elvira Ojanguren López, Esaúl Ruíz Narbona, Roberto Torre Alonso, Marta Tío Sáenz & Raquel Vea Escarza. 2024. Nerthusv5. Interface of textual, lexicographical and secondary sources of Old English. Nerthus Project, Universidad de La Rioja, www.nerthusproject.com.

Cite ParCorOEv3 as:

> Martín Arista, Javier (ed.), Sara Domínguez Barragán, Luisa Fidalgo Allo, Laura García Fernández, Yosra Hamdoun Bghiyel, Miguel Lacalle Palacios, Raquel Mateo Mendaza, Carmen Novo Urraca, Ana Elvira Ojanguren López, Esaúl Ruíz Narbona, Roberto Torre Alonso & Raquel Vea Escarza. 2023. ParCorOEv3. An open access annotated parallel corpus Old English-English. Nerthus Project, Universidad de La Rioja, www.nerthusproject.com.

## Related

- [[concepts/old-english-form-generation]]
- [[concepts/old-english-lemmatisation]]
- [[references/martin-arista-2026-oe-lemmatisation]]
- [[synthesis/Research: Old English Morphology Generation]]

## Sources

- [Nerthus home](https://www.nerthusproject.com/)
- [About us](https://www.nerthusproject.com/about-us)
- [Nerthus version history](https://www.nerthusproject.com/previous-versions-1)
- [Nerthus v5 database description](https://www.nerthusproject.com/database-description)
- [Search Nerthus v5](https://www.nerthusproject.com/search-nerthusv5)
- [How to cite Nerthus v5](https://www.nerthusproject.com/how-to-cite-2)
- [ParCorOEv3 corpus description](https://www.nerthusproject.com/corpus-description)
- [ParCor methodology](https://www.nerthusproject.com/corpus-methodology)
- [ParCor version history](https://www.nerthusproject.com/previous-versions)
- [How to cite ParCor](https://www.nerthusproject.com/how-to-cite)
- [CoRD Nerthus v3](https://varieng.helsinki.fi/CoRD/corpora/Nerthus/structure.html)
- [UD_Old_English-OEDT](https://github.com/dmetola/Old_English-OEDT)
