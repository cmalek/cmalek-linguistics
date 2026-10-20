---
title: >-
  OldEnglishMorphology (OntoLex and SHACL)
category: references
tags: [old-english, morphology, ontolex, shacl, strong-verbs]
relationships:
  - target: "[[concepts/old-english-inflectional-class]]"
    type: related_to
  - target: "[[projects/wyrdcraeft/concepts/morphology-generation]]"
    type: related_to
  - target: "[[references/oe-wordnet-repos]]"
    type: related_to
sources:
  - "repo:github.com/anasfkhan81/OldEnglishMorphology"
source_url: "https://github.com/anasfkhan81/OldEnglishMorphology"
summary: >-
  Proof of concept modelling 13 Old English strong verbs in OntoLex-Lemon, with SHACL SPARQL shapes enforcing ablaut-vowel patterns per class. The shapes are the idea worth taking, not the data.
provenance:
  extracted: 0.85
  inferred: 0.15
  ambiguous: 0.0
base_confidence: 0.45
lifecycle: draft
lifecycle_changed: "2026-10-15"
tier: supporting
created: 2026-10-15T00:00:00Z
updated: 2026-10-15T00:00:00Z
snapshots:
  - "[[_raw/_archived/GITHUB OldEnglishMorphology 2026-10-15|GITHUB OldEnglishMorphology 2026-10-15]]"
---

# OldEnglishMorphology (OntoLex and SHACL)

Claimed as OntoLex-Lemon modelling of Clark-Hall strong-verb morphology. In practice: one commit (2026-03-11), 13 hand-written verbs (`bīdan`, `faran`, `niman`, `sprecan`, and nine more), Apache-2.0, placeholder namespace `https://example.org/chm#`.

## Pieces

- `clark_hall_strong_verb_classes_chm_ontology.ttl` (57 KB): `chm:StrongVerb` as subclass of `ontolex:LexicalEntry` and `lexinfo:Verb`; classes I–VII with subclasses (IIa, IIb, IIIa–e, VIIa, VIIb). Each entry has a canonical form (the infinitive) and `ontolex:otherForm` nodes carrying `lexinfo` tense, person, number, mood, and a custom `chm:rootVowel`. Variants are separate nodes (`bīdan` has three 2sg present forms).
- `clark_hall_shapes.ttl` (43 KB): 63 `sh:sparql` constraints in ten node shapes. Example: class I needs ī in the infinitive, ā in preterite singular, i in preterite plural and past participle. No shapes yet for IIb, VIIa, VIIb.
- `validate_shacl.py`: a pyshacl runner. IDs are ASCII-folded (`biidan`).

## Limits

The vowel constraints ignore consonant alternations, SPARQL cannot generate forms, and there are no weak or irregular verbs and no lexicon.

## Use for wyrdcraeft

Port the ablaut constraints over (infinitive, preterite singular, preterite plural, past participle) as unit tests for generated strong-verb tables, in the spirit of the oracle tests in [[references/btc-anglo-saxon]]. The OntoLex plus LexInfo pattern is a template if RDF export is ever wanted. See [[concepts/old-english-form-generation]].

## Sources

- [[_raw/_archived/GITHUB OldEnglishMorphology 2026-10-15]]
- Repo read directly on 2026-10-15 (shallow clone, nothing executed).
