---
title: >-
  Old English dictionary repos on GitHub
category: references
tags: [old-english, dictionary, bosworth-toller, lexicon]
relationships:
  - target: "[[entities/bosworth-toller]]"
    type: uses
  - target: "[[references/btc-anglo-saxon]]"
    type: related_to
  - target: "[[projects/wyrdcraeft/concepts/dictionary-build]]"
    type: related_to
sources:
  - "repo:github.com/furrykef/oedict"
  - "repo:github.com/loco-lab/OEDict"
  - "repo:github.com/BenjaminTMilnes/BosworthAndToller"
  - "repo:github.com/vkkokko/oldenglishonline"
summary: >-
  Four dictionary-adjacent repos: a small curated lexicon with an inflection generator, a 58k-row Bosworth-Toller CSV conversion, an abandoned BT parser, and a static course site.
provenance:
  extracted: 0.86
  inferred: 0.14
  ambiguous: 0
base_confidence: 0.5
lifecycle: draft
lifecycle_changed: "2026-10-15"
tier: supporting
created: 2026-10-15T00:00:00Z
updated: "2026-10-18T19:48:28.152600+00:00"
snapshots:
  - "[[_raw/_archived/GITHUB oedict 2026-10-15|GITHUB oedict 2026-10-15]]"
  - "[[_raw/_archived/GITHUB OEDict 2026-10-15 1|GITHUB OEDict 2026-10-15 1]]"
  - "[[_raw/_archived/GITHUB BosworthAndToller 2026-10-15|GITHUB BosworthAndToller 2026-10-15]]"
  - "[[_raw/_archived/GITHUB oldenglishonline 2026-10-15|GITHUB oldenglishonline 2026-10-15]]"
  - "[[_raw/_archived/GITHUB BosworthAndToller 2026-10-15-1|GITHUB BosworthAndToller 2026-10-15-1]]"
---

# Old English dictionary repos on GitHub

| Repo | What it really is | Licence | Last commit |
|---|---|---|---|
| furrykef/oedict | Hand-curated learner lexicon (about 3,400 entries), inflection generator, SQLite index, Flask API | none | 2024-11-26 |
| loco-lab/OEDict | Data conversion of Crist's Bosworth-Toller text to a 58k-row CSV and an Apple Dictionary | MIT (code); source text states free redistribution | 2020-06-01 |
| BenjaminTMilnes/BosworthAndToller | Abandoned partial BT entry parser | none | 2021-12-27 |
| vkkokko/oldenglishonline | Static course site with exercises | MIT code, CC BY-SA 3.0 content | 2025-07-16 |

## furrykef/oedict

Entries are `lemma, wordtype: specials` plus indented glosses (`lexicon.txt`, 129 KB). `oedict/lexicon.py` parses them and generates inflected forms (`gen_noun`, `gen_verb`, and so on) and spelling variants; `lexdb.py` rebuilds a SQLite index mapping every generated form to its entry, so `hyran` finds `hīeran`. About 365 entries are bare `SEE x` redirects. The README says [[entities/bosworth-toller|Bosworth-Toller]] and Sweet were used for glosses, with no explicit licence, so glosses have mixed provenance. The author calls the variant generator "a bit of a joke". No tests. The tag scheme and conservative Early West Saxon headwords with variant folding are worth studying.

## loco-lab/OEDict

Not a parser. `sources/oe_bosworthtoller.txt` (30.8 MB) is the partially corrected 2007 Crist/Kurisuto text covering Bosworth-Toller (1898) and Toller's 1921 Supplement. A 35-line `json_to_csv.py` flattens a JSON file that is not in the repo; `oe_bt.csv` keeps raw `<B>`/`<I>` markup in the definition field. Useful as a quick flat table; needs tag stripping.

## BosworthAndToller (Milnes)

The README is a title. `compile.py` defines `Page`, `Entry`, `Example` classes and a hand-rolled scanner built on the author's own `tauparsing` library, which is missing. The loop is hard-coded to four pages, and sample output is wrong (`æfen-þénung` puts the whole gloss in a Latin field). Take only `bosworth_and_toller_abbreviations.json` (136 KB of citation abbreviations). The same abbreviation list, from the same Crist data, appears in [[references/btc-anglo-saxon]] and in wyrdcraeft.

## oldenglishonline

A Gulp-built static site (EJS, jQuery) with about 91 lesson pages and about 190 JSON files: graded exercises with explained answers and common mistakes, and small POS-labelled vocabularies. No lexicon, morphology engine, or BT link. The sentence exercises could serve as a small CC BY-SA gold set for checking paradigm generation.

## Takeaway for wyrdcraeft

Only the Crist text is large, and it is unstructured. Structuring BT entries is the problem that [[projects/wyrdcraeft/concepts/dictionary-build]] is already solving; Milnes's attempt failed, and [[references/btc-anglo-saxon]] is the strongest prior art.

## Additional clipped inventory

The annotated clip identifies XML as well as JSON abbreviation mappings, a conversion script whose OCR input is absent, and partial example output from the A section. These additions refine the inventory above; they do not demonstrate that the parser produces a complete dictionary.

## Sources

- [[_raw/_archived/GITHUB oedict 2026-10-15]]
- [[_raw/_archived/GITHUB OEDict 2026-10-15 1]]
- [[_raw/_archived/GITHUB BosworthAndToller 2026-10-15]]
- [[_raw/_archived/GITHUB oldenglishonline 2026-10-15]]
- Repos read directly on 2026-10-15 (shallow clones, nothing executed).
- [[_raw/_archived/GITHUB BosworthAndToller 2026-10-15-1.md]]
