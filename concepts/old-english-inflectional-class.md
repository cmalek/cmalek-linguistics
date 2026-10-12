---
title: >-
  Old English inflectional class
category: concepts
tags: [old-english, morphology, grammar]
relationships:
  - target: "[[concepts/old-english-grammar]]"
    type: extends
  - target: "[[projects/wyrdcraeft/concepts/wright-catalog]]"
    type: related_to
  - target: "[[references/nerthus-v5-database]]"
    type: derived_from
  - target: "[[references/tichy-2017-morphological-analyser]]"
    type: related_to
sources:
  - "url:https://www.nerthusproject.com/database-description"
  - "url:https://varieng.helsinki.fi/CoRD/corpora/Nerthus/structure.html"
  - "url:https://casopispromodernifilologii.ff.cuni.cz/wp-content/uploads/sites/9/2017/06/Ondřej_Tichý_40-54.pdf"
summary: >-
  Stem class is a lexical field: Nerthus stores it, Tichý explodes verbs to 132 machine classes, UPOS tags omit it.
provenance:
  extracted: 0.80
  inferred: 0.15
  ambiguous: 0.05
base_confidence: 0.74
lifecycle: draft
lifecycle_changed: 2026-10-09
tier: supporting
created: 2026-10-09T19:50:00Z
updated: 2026-10-09T19:50:00Z
---

# Old English inflectional class

Part of speech says “verb” or “noun.” Inflectional class says which paradigm: strong III, weak II, masculine a-stem, and so on. Generation needs the second. A UPOS tag does not carry it.

## Where the class labels live

[[references/nerthus-v5-database|Nerthus v5]] defines part of speech as lexical category **and** inflectional class. In v3 the class labels were copied from Clark Hall, Bosworth–Toller, and Sweet, and explicitly not from the Dictionary of Old English. Strong-verb subclasses follow Krygier (1994). The published sample is *āblinnan*, “strong III,” with the alternative spellings kept on the same entry. Adjectival comparison follows Seelig (1930).

[[references/tichy-2017-morphological-analyser|Tichý (2017)]] starts from the same dictionaries and then splits verbs further. He keeps Wright’s exemplar paradigms and, where the textbook has seven strong classes, three weak classes, and a few irregulars, the implementation has **132 verb classes**. Assignment is a string match against exemplar lemmas, then rules that use syllable count and stem length computed at load time. A successful analysis names the class in the output: *andswarodon* is weak 2, subtype a, pattern *sealfian*.

[[entities/dictionary-of-old-english|DOE]] entries, as [[references/computational-study-of-old-english-2025|Martín Arista (2025)]] describes them, carry part of speech and gender, and strong or weak when the word is a noun or a verb, plus a FORM line of attested spellings. That is coarser than Krygier’s subclasses and coarser than Tichý’s 132.

[[projects/wyrdcraeft/concepts/wright-catalog|Wright’s catalog]] in wyrdcraeft is this same layer: class labels from the grammar, attached to dictionary lemmas before any form is written.

## What taggers return instead

[[references/martin-arista-2026-oe-lemmatisation|The 2026 lemmatiser]] returns UPOS. Verb accuracy on that task is about 55 percent, and the card assigns about a quarter of the errors to strong-verb ablaut. [[references/miani-2025-oe-poetry-pos|Miani, Stymne, and Darwin]] show that mapping YCOE’s hundreds of tags onto UPOS throws away case, gender, and number. Class is already gone before that mapping. YCOE’s own tags encode case, number, tense, and mood on the token. They do not store “this noun is an i-stem.”

## Assigning a class to a word the dictionary lacks

For a simplex already in Nerthus or Bosworth–Toller, copy the class field. For a compound, the attested dictionaries enter it as its own headword when a lexicographer has seen it. When they have not, the class has to be inherited from the morphological head, which in Old English compounds is normally the second element, the first being uninflected ([[concepts/oe-word-formation]]). ^[inferred] Prefixes such as *ge-*, *ā-*, *be-*, *for-* change transitivity and aspect more often than they change the inflectional class of the verb. Nerthus’s simplex headword ignores *ge-* for that reason. The class of *ge-beran* is the class of *beran*. ^[inferred]

Gender is part of the nominal class record. Tichý’s Table 6 splits 19,835 noun lemmas into 8,668 masculine, 7,306 feminine, and 4,067 in the remaining gender row.

## Related

- [[concepts/old-english-form-generation]]
- [[concepts/old-english-grammar]]
- [[skills/oe-paradigm-lookup]]

## Sources

- [[references/nerthus-v5-database]]
- [[references/tichy-2017-morphological-analyser]]
- [[references/martin-arista-2026-oe-lemmatisation]]
- [[references/computational-study-of-old-english-2025]]
