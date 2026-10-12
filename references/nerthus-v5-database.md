---
title: >-
  Nerthus v5 lexical database
category: references
tags: [old-english, lexicography, morphology]
sources:
  - "url:https://www.nerthusproject.com/database-description"
  - "url:https://www.nerthusproject.com/how-to-cite-2"
  - "url:https://www.nerthusproject.com/previous-versions-1"
  - "url:https://www.nerthusproject.com/search-nerthusv5"
  - "url:https://varieng.helsinki.fi/CoRD/corpora/Nerthus/structure.html"
source_url: "https://www.nerthusproject.com/database-description"
relationships:
  - target: "[[entities/nerthus-project]]"
    type: related_to
  - target: "[[skills/using-nerthus]]"
    type: related_to
  - target: "[[concepts/old-english-inflectional-class]]"
    type: implements
  - target: "[[concepts/old-english-form-generation]]"
    type: related_to
  - target: "[[concepts/oe-word-formation]]"
    type: extends
summary: >-
  Nerthus v5 (2024): 32,812 headwords, class, attested forms, derivation, and a dictionary comparison.
provenance:
  extracted: 0.86
  inferred: 0.10
  ambiguous: 0.04
base_confidence: 0.62
lifecycle: draft
lifecycle_changed: 2026-10-09
tier: supporting
created: 2026-10-09T19:50:00Z
updated: 2026-10-09T20:32:00Z
---

# Nerthus v5 lexical database

[Nerthus v5 database description](https://www.nerthusproject.com/database-description), Javier Martín Arista and the [[entities/nerthus-project|Nerthus Project]], University of La Rioja. Headword spelling follows Clark Hall. The Helsinki CoRD page documents the earlier Nerthus v3 file (2016). Guest search: [[skills/using-nerthus]]. The live door is [https://muga.unirioja.es/fmi/webd/ONLINENerthusV5.fmp12](https://muga.unirioja.es/fmi/webd/ONLINENerthusV5.fmp12).

Cite it as the project asks: Martín Arista, Javier (ed.), Sara Domínguez Barragán, Luisa Fidalgo Allo, Laura García Fernández, Yosra Hamdoun Bghiyel, Miguel Lacalle Palacios, Raquel Mateo Mendaza, Carmen Novo Urraca, Ana Elvira Ojanguren López, Esaúl Ruíz Narbona, Roberto Torre Alonso, Marta Tío Sáenz & Raquel Vea Escarza. 2024. *Nerthusv5. Interface of textual, lexicographical and secondary sources of Old English.* Nerthus Project, Universidad de La Rioja, www.nerthusproject.com.

The version page says v5 adds four things v3 did not publish together: a dictionary interface comparing current Old English dictionaries; attested inflectional forms from morphological generation for every inflecting class; secondary-source references on the headword; and a ParCorOEv3 citation for each headword the corpus contains. v4 was an unpublished transition.

## v5, six blocks

- **32,812 headword files.** Three headword shapes: a simplex that ignores *ge-*, an alphabetical headword, and a numbered headword that splits homographs and alternative spellings.
- Meaning from Sweet, Clark Hall, and [[entities/bosworth-toller|Bosworth–Toller]], plus a synthetic definition. [[entities/dictionary-of-old-english|DOE]] headwords are linked for A–I.
- Part of speech is **lexical category plus inflectional class**. That is the field a generator needs and a UPOS tag does not provide. See [[concepts/old-english-inflectional-class]].
- Four inflection lists: forms printed in Bosworth–Toller, forms from secondary sources, forms in ParCorOEv3, and **automatically generated canonical forms that are attested in the DOEC**. Generation here is filtered by attestation, the same choice [[references/tichy-2017-morphological-analyser|Tichý]] makes.
- Derivational morphology, syntagmatic and paradigmatic: base, category of the base, affix, and a lexical prime. Every non-basic word is affixation, zero derivation, affixless derivation, or compounding. See [[concepts/oe-word-formation]].
- One ParCorOEv3 citation per headword, with a Present-Day English translation, plus an index of secondary literature.

## v3 counts and class sources

CoRD’s structure page for Nerthus v3 records **31,298** files:

| Category | Files |
|---|---|
| noun | 17,666 |
| adjective | 5,359 |
| verb | 5,833 |
| adverb | 1,468 |
| proper name | 496 |
| affix | 113 |
| hypothetical | 65 |
| other | 298 |

Inflectional classes and forms were taken from Clark Hall, Bosworth–Toller (with Toller’s supplement and Campbell’s addenda), and Sweet. The DOE was **not** a source of class labels. Comparatives and superlatives follow Seelig (1930). Strong-verb subclasses follow Krygier, *The Disintegration of the English Strong Verb System* (1994). The sample row is *āblinnan*, alternative spellings *āblynnan, onblinnan*, category verb, inflectional morphology **strong III**.

Hypothetical predicates are capped at 65. A hypothetical form is allowed only when the source, the target, and the process are each attested elsewhere. That is a closed derivational lexicon, not an open compound generator.

## Related

- [[concepts/old-english-lemmatisation]]
- [[references/martin-arista-2026-oe-lemmatisation]]
- [[references/computational-study-of-old-english-2025]]

## Sources

- [Nerthus v5 database description](https://www.nerthusproject.com/database-description)
- [How to cite Nerthus v5](https://www.nerthusproject.com/how-to-cite-2)
- [Nerthus version history](https://www.nerthusproject.com/previous-versions-1)
- [Search Nerthus v5](https://www.nerthusproject.com/search-nerthusv5)
- [CoRD: Nerthus v3 structure](https://varieng.helsinki.fi/CoRD/corpora/Nerthus/structure.html)
