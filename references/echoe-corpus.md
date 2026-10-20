---
title: >-
  ECHOE corpus
category: references
tags: [old-english, corpus, tei, homilies]
relationships:
  - target: "[[concepts/old-english-orthographic-variation]]"
    type: related_to
  - target: "[[entities/wulfstan-of-york]]"
    type: related_to
  - target: "[[references/old-english-texts-iswoc]]"
    type: related_to
sources:
  - "repo:github.com/ECHOEProject/echoe"
source_url: "https://github.com/ECHOEProject/echoe"
summary: >-
  TEI P5 corpus of anonymous and Wulfstanian Old English homilies and prose hagiography: 337 versions, about 553k tokens, diplomatic transcription with no lemma or POS tags, GPL-3.0.
provenance:
  extracted: 0.85
  inferred: 0.1
  ambiguous: 0.05
base_confidence: 0.55
lifecycle: draft
lifecycle_changed: "2026-10-15"
tier: supporting
created: 2026-10-15T00:00:00Z
updated: 2026-10-15T00:00:00Z
snapshots:
  - "[[_raw/_archived/GITHUB echoe 2026-10-15|GITHUB echoe 2026-10-15]]"
---

# ECHOE corpus

A data and documentation repo, not an application. `xml/NNN.NN.xml` holds 337 files, one per Ker manuscript article, across 60 manuscripts: 33,866 sentences and 553,249 tokens (`metadata/corpus_stats.json`).

## Structure

- Each file has a full `teiHeader` (`msDesc`, hand, date, licence). The body is `<s xml:id="s18.40.1">` sentences of `<w>` tokens.
- Palaeographic encoding is heavy: `abbr/expan/am/ex`, `choice`, `subst/add/del`, `lb/pb`. MUFI private-use characters are declared per file (see [[references/mufi-character-recommendation]]). Schema: `misc/echoe.odd` and `echoe.rng`.
- Metadata JSON: Bible references, motifs, persons, places, demonyms, cross-references.
- `misc/xml2txt.py` (lxml) builds `plaintext/*.txt`, one `id: sentence` line per sentence. It lowercases and folds `ƿ→w`, `ſ→s`, `v→u`, `j→i`, `&→et`, `ę→æ`, and drops abbreviation and deletion markup.

## Limits

- No lemma or POS annotation; tokens are diplomatic text only.
- The plaintext normalisation is lossy and keeps no macrons or ġ/ċ. Orthography is late and transitional (up to s. xii), not standard West Saxon.
- GPL-3.0 (copyleft). Last commit 2026-06-12. No tests.

## Use

A large, recent, sentence-segmented prose corpus for spelling-variation, normalisation, or tokenisation work. Lemmas would have to be supplied, for example by wyrdcraeft. Homilies of [[entities/wulfstan-of-york]] and others make it relevant to [[concepts/institutes-of-polity]] work. ^[inferred]

## Sources

- [[_raw/_archived/GITHUB echoe 2026-10-15]]
- Repo read directly on 2026-10-15 (shallow clone, nothing executed).
