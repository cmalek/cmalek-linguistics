---
title: >-
  Old English case government
category: concepts
tags: [old-english, syntax, valency]
relationships:
  - target: "[[references/ycoe-case-and-pos-annotation]]"
    type: derived_from
  - target: "[[references/paveda-old-english-valency]]"
    type: derived_from
  - target: "[[concepts/old-english-grammar]]"
    type: extends
sources:
  - "url:https://www-users.york.ac.uk/~lang18/Documentation/pos-manual-oe.htm"
  - "url:https://paveda.unipv.it/contributions/olde1238"
summary: >-
  Verb and preposition case frames are lexical. YCOE will not infer them; PaVeDa codes them for 80 ValPaL meanings.
provenance:
  extracted: 0.78
  inferred: 0.16
  ambiguous: 0.06
base_confidence: 0.72
lifecycle: draft
lifecycle_changed: 2026-10-09
tier: supporting
created: 2026-10-09T19:50:00Z
updated: 2026-10-09T19:50:00Z
---

# Old English case government

Government (rection) is which case a verb or a preposition requires of its complement. It is a property of the lexical item, not of the noun’s inflectional class. A noun generator can emit dative singular *cyninge* without knowing that *helpan* takes the dative. Linking the two is a lexicon of frames.

## What the parsed corpus actually did

The [[references/ycoe-case-and-pos-annotation|YCOE manual]] marks case when the ending distinguishes it. It does **not** relabel an ambiguous ending from the governor’s usual case. An accusative/dative object of a dative verb stays unmarked. The one systematic exception is dative/genitive: if the governor is not on the list of genitive-takers, the complement is called dative. The manual cites Mitchell, *Old English Syntax* (1985), for that list, and says the policy exists because a reliable requirement was not available for every verb.

Prepositions follow the same rule. Accusative/dative ambiguity is never resolved. *tō* is treated as mostly dative, so only an unambiguous genitive is labelled genitive. *wiþ* is treated as mixed, so only unambiguous forms are labelled. First- and second-person pronouns are left unlabelled for case in most prose, because the forms themselves do not distinguish accusative and dative.

So the largest treebank is evidence of **attested case on unambiguous forms**. It is not a government dictionary.

## The valency sample

[[references/paveda-old-english-valency|PaVeDa]] is the resource that writes the frames down. Martina Giarda coded the 80 ValPaL meanings against YCOE and YCOEP, with lemmas from Bosworth–Toller and the DOE. Frames look like `1-nom V.subj[1] 2-dat 3-acc`, with prepositional alternations (`of+NP-dat`, *tō* plus dative, *on*, *mid*, *fram*) and a *be-* alternation. Nominative, accusative, genitive, and dative are the working cases. Instrumental is residual. Ditransitives are usually indirective.

Eighty meanings cover the typological questionnaire. They do not cover the verbal lexicon of Bosworth–Toller, and they do not list, for each preposition, the cases it governs across all verbs.

Goh’s work on Old English preposition–verb compounds (the obliqueness hierarchy: accusative less oblique than dative or genitive) explains why a compound such as *wiþ-bregdan* takes the case it takes. It is an analysis of inheritance in compounding, not a table of frames.

## Practical consequence

A full government layer has to be built as its own lexicon. The seed is PaVeDa’s 80 frames plus Mitchell’s genitive-verb list as used by YCOE. Extending it to every verb and every preposition is still open. Prefixes change government as well as meaning: Nerthus publications (Ruiz Narbona on *for-* and *ge-*, and on *ā-* and *ge-*) treat prefixation as a transitivity change, so a frame on the simplex does not automatically transfer to the prefixed verb. ^[inferred]

## Related

- [[concepts/old-english-form-generation]]
- [[concepts/oe-word-formation]]
- [[entities/paveda]]
- [[entities/ycoe]]

## Sources

- [[references/ycoe-case-and-pos-annotation]]
- [[references/paveda-old-english-valency]]
- [[references/nerthus-v5-database]]
