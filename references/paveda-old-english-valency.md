---
title: >-
  PaVeDa Old English valency
category: references
tags: [old-english, syntax, valency]
sources:
  - "url:https://paveda.unipv.it/contributions/olde1238"
source_url: "https://paveda.unipv.it/contributions/olde1238"
relationships:
  - target: "[[entities/paveda]]"
    type: related_to
  - target: "[[concepts/old-english-case-government]]"
    type: implements
  - target: "[[entities/ycoe]]"
    type: uses
summary: >-
  PaVeDa codes Old English case frames for the 80 ValPaL verb meanings, from YCOE and YCOEP, including preposition plus case.
provenance:
  extracted: 0.84
  inferred: 0.12
  ambiguous: 0.04
base_confidence: 0.62
lifecycle: draft
lifecycle_changed: 2026-10-09
tier: supporting
created: 2026-10-09T19:50:00Z
updated: 2026-10-09T19:50:00Z
---

# PaVeDa Old English valency

[PaVeDa Old English contribution](https://paveda.unipv.it/contributions/olde1238), Martina Giarda, University of Pavia and University of Bergamo. Glottocode `olde1238`, ISO 639-3 `ang`. Collected in the second half of 2022 and in 2023.

## What is coded

The database holds coding frames for the **80 core meanings** of ValPaL. Each frame lists the arguments of a predefined role set with Old English case, plus a few extra arguments that showed up regularly. Verb lemmas were chosen from the electronic [[entities/bosworth-toller|Bosworth–Toller]] and the [[entities/dictionary-of-old-english|Dictionary of Old English]]. Examples come from a subset of [[entities/ycoe|YCOE]] (Taylor et al. 2003) and YCOEP (Pintzuk and Plug 2002). If the sample lacked a clear example, Giarda took one from elsewhere in the treebanks or from the dictionaries.

Case inventory in the contribution’s own wording: nominative, accusative, genitive, and dative, with residual instrumental. Nominative marks S and A and is indexed on the verb. Accusative marks the direct object and some adverbials of extent. Dative marks the indirect object (mainly R) and also possession and adverbial uses. Genitive is adnominal and adverbial. Accusative, dative, and genitive all occur in prepositional phrases. The most common adposition pattern named on the page is *tō* plus dative.

Ditransitives are usually indirective. TEACH allows neutral alignment and FILL allows secundative alignment, in the contribution’s terms.

Published coding sets include bare `NP-dat` and `of+NP-dat`, with frames such as `1-nom V.subj[1] of 2-dat`. A basic three-place frame on the site is `1-nom V.subj[1] 2-dat 3-acc`, with a prepositional alternation and a *be-* alternation. Those alternations are the government facts [[concepts/old-english-case-government]] asks for, on a sample of meanings rather than on the whole lexicon.

## Limits

Eighty meanings is a typological sample, not every Bosworth–Toller verb. Prepositions appear as flags on those frames (`of`, `on`, `tō`, `mid`, `fram`), not as a standalone government table for every preposition. Word order is described, citing Mitchell and Robinson and van Kemenade, and is not itself a case frame.

## Related

- [[references/ycoe-case-and-pos-annotation]]
- [[concepts/old-english-case-government]]
- [[entities/paveda]]

## Sources

- [PaVeDa: Old English](https://paveda.unipv.it/contributions/olde1238)
