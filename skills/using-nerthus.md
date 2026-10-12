---
title: >-
  Using Nerthus
category: skills
tags: [old-english, lexicography, workflow]
relationships:
  - target: "[[entities/nerthus-project]]"
    type: uses
  - target: "[[references/nerthus-v5-database]]"
    type: uses
  - target: "[[concepts/old-english-inflectional-class]]"
    type: related_to
  - target: "[[concepts/old-english-case-government]]"
    type: related_to
  - target: "[[entities/paveda]]"
    type: related_to
sources:
  - "url:https://www.nerthusproject.com/search-nerthusv5"
  - "url:https://www.nerthusproject.com/search-parcoroe"
  - "url:https://www.nerthusproject.com/database-description"
  - "url:https://www.nerthusproject.com/corpus-description"
summary: >-
  Guest search of Nerthus v5 and ParCorOEv3: class, spellings, prose tokens, and the fields neither database stores.
provenance:
  extracted: 0.88
  inferred: 0.08
  ambiguous: 0.04
base_confidence: 0.70
lifecycle: draft
lifecycle_changed: 2026-10-09
tier: supporting
created: 2026-10-09T20:32:00Z
updated: 2026-10-09T20:32:00Z
---

# Using Nerthus

Open the database in a browser whose preferred language is English. The project’s search pages say FileMaker follows that language. Both hosts below returned HTTP 200 on 9 October 2026. That check did not sign in.

| Database | Door | Instructions |
|---|---|---|
| Nerthus v5 | https://muga.unirioja.es/fmi/webd/ONLINENerthusV5.fmp12 | https://www.nerthusproject.com/search-nerthusv5 |
| ParCorOEv3 | https://muga.unirioja.es/fmi/webd/ONLINEParcor.fmp12 | https://www.nerthusproject.com/search-parcoroe |

Background, counts, and citations: [[entities/nerthus-project]]. Field inventory: [[references/nerthus-v5-database]].

## Key Ideas

**Sign in and find.** Choose Sign In as Guest. Then View → Find Mode. Type the query in the field that matches it. The +/= menu on a field holds the wildcards. The project points at FileMaker’s own operator list for the symbols, and this page does not restate them. Press Perform. Further requests go through the Request button or Requests in the main menu. Constrain Find keeps hits inside the current found set. Extend Find adds hits. Quick Find searches every field at once. Show All Records clears the found set. Browse Mode leaves Find Mode. The same gestures apply to ParCor.

**Look up class.** On a Nerthus headword, read lexical category and inflectional class together. That is the class a generator copies ([[concepts/old-english-inflectional-class]]). Strong-verb subclasses in v3 follow Krygier (1994). The published sample is *āblinnan*, strong III.

**Choose the headword shape.** The simplex search ignores *ge-*. The alphabetical headword is the citation form. The numbered headword splits homographs and alternative spellings. For a prefixed verb, search the whole string (*æt-swymman*), because prefixed verbs are headwords in this lexicon and in Tichý’s. For a compound, search the whole string. No hit means that string is outside the 32,812 files. Class then comes from the right-hand head, and the compound is a candidate to generate, not a row to copy.

**Read the four form lists as attestation.** Bosworth–Toller forms, secondary-source forms, ParCor forms, and generated canonical forms that also occur in the DOEC. A missing cell in those lists is a missing attestation. It is still a grammatical cell if the class predicts it. Alternative spellings are variants on the headword. They are not tagged West Saxon, Anglian, or Kentish.

**Use ParCor for a prose token.** Search the form or the lemma. A hit gives the token, file number, lemma, lexical category, inflectional category, gloss, concordance, Present-Day English translation, and sources. The 2023 field name is inflectional category. Stem class stays on the Nerthus headword. The corpus is the seventeen prose texts listed on [[entities/nerthus-project]]. A poetic hapax will not be there.

**Leave these questions to other pages.** Case government is not in either database. Use [[entities/paveda|PaVeDa]] and [[concepts/old-english-case-government]]. Dialect-labeled paradigms are not in the form lists. Use [[concepts/old-english-orthographic-variation]] and [[concepts/old-english-dialects]]. The GitHub treebank is a 50,000-word dependency sample of five ParCor texts, license CC BY-SA 4.0. It is not a download of the lexicon.

## Open Questions

- Whether a guest WebDirect session can export the found set. The project pages do not say.
- Whether v5 still caps hypothetical derivatives at the 65 files CoRD records for v3.

## Sources

- [Search Nerthus v5](https://www.nerthusproject.com/search-nerthusv5)
- [Search ParCorOE](https://www.nerthusproject.com/search-parcoroe)
- [Nerthus v5 database description](https://www.nerthusproject.com/database-description)
- [ParCorOEv3 corpus description](https://www.nerthusproject.com/corpus-description)
