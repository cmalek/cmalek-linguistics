---
title: >-
    Bosworth-Toller
category: entities
tags: [old-english, lexicography, tools]
relationships:
  - target: "[[entities/walter-william-skeat]]"
    type: related_to
  - target: "[[skills/translating-ancient-texts]]"
    type: uses
  - target: "[[concepts/old-english]]"
    type: related_to
  - target: "[[projects/wyrdcraeft/concepts/dictionary-build]]"
    type: related_to
  - target: "[[entities/ondrej-tichy]]"
    type: related_to
  - target: "[[synthesis/Research: Old English Morphology Generation]]"
    type: related_to
sources:
  - "agent:raw-scan Bosworth-Toller p. 27 A-FLYGE - A-GǢLAN"
summary: "The Anglo-Saxon Dictionary: headword, gender, Latin gloss, and cited OE passages. Page 27 shows the a- prefix cluster from a-flyge through a-fyllan."
provenance:
  extracted: 0.88
  inferred: 0.10
  ambiguous: 0.02
base_confidence: 0.59
lifecycle: draft
lifecycle_changed: "2026-09-25"
tier: supporting
created: 2026-09-25T16:55:00Z
updated: 2026-10-09T19:50:00Z
snapshots:
  - "[[_raw/_archived/Bosworth-Toller p. 27 A-FLYGE - A-GǢLAN|Bosworth-Toller p. 27 A-FLYGE - A-GǢLAN]]"
---

# Bosworth-Toller

Joseph Bosworth’s *An Anglo-Saxon Dictionary*, completed and enlarged by T. Northcote Toller — the default historical dictionary named in [[skills/translating-ancient-texts]]. Cambridge’s Elrington and Bosworth chair (held by [[entities/walter-william-skeat]]) is a related namesake, not the same book. ^[inferred]

## Key Ideas

A typical entry (p. 27, *a-flyge* → *a-fyllan*) packs:

- Headword with length marks and hyphen showing the prefix (*a-flýman*).
- Grammatical label (*m.*, *n.*, *v. trans.*) and principal parts (*p.* / *pp.*).
- Modern English gloss plus a Latin equivalent (*fugare*, *suscipere*).
- Brief etymological pointers (*Ger. Flug*, Goth. *abrs*, ON *æfr*).
- **Citations** into the corpus: *Battle of Maldon* (*Byrht.*), Genesis, Orosius, Bede, *Judith*, *Exeter Book*, Psalms, laws.

Worked examples from this leaf: *a-flýman* “put to flight” (Maldon 243); *afor* “vehement” of Judith; *afora* cross-ref to *eafora* “son”; *a-fón* “receive/seize”; *a-fréfran* “comfort.” Prefix *a-* is sometimes intensive (*a-forhtian*).

The scan is messy (OCR, mixed type). Prefer a modern digital Bosworth-Toller (bosworthtoller.com / DOE when available) for quoting. ^[inferred]

## Related

- [[synthesis/oe-prefixes-for-fore-oth-x-bosworth-toller|Old English for-, fore-, and oþ- Prefixes × Bosworth-Toller]] — synthesis
- [[projects/wyrdcraeft/concepts/dictionary-build]] — how this toolkit parses a Bosworth-Toller source file into SQLite.
- [[projects/wyrdcraeft/concepts/dictionary-query-and-browse]] — lookup and the read-only browse shell over that index.

## As a generator lexicon

[[entities/ondrej-tichy|Ondřej Tichý]]’s 2017 analyser takes this dictionary as the lemma list, on the ground that it is the only one that at least theoretically covers the whole lexicon. The online edition at bosworthtoller.com is his digitization. Campbell’s 1972 addenda are not in it. [[entities/dictionary-of-old-english|The Dictionary of Old English]] is written from the corpus and is still incomplete, so the two lists are not the same inventory. Compounds that occur once in poetry are the lemmas a Bosworth–Toller-only generator misses. See [[synthesis/Research: Old English Morphology Generation]].

## Open Questions

- How this page’s lemmas map onto the *Dictionary of Old English* A–I coverage.

## Sources

- Bosworth-Toller dictionary, p. 27 (*a-flyge*–*a-fyllan*)
