---
title: "Bosworth-Toller × Dictionary build"
category: synthesis
tags: ["old-english", "lexicography", "wyrdcraeft"]
sources:
  - "entities/bosworth-toller.md"
  - "projects/wyrdcraeft/concepts/dictionary-build.md"
  - "references/btc-anglo-saxon.md"
  - "references/oe-dictionary-repos.md"
  - "projects/wyrdcraeft/wyrdcraeft.md"
  - "projects/wyrdcraeft/concepts/source-conversion.md"
  - "projects/wyrdcraeft/concepts/dictionary-query-and-browse.md"
  - "sources/germanic-lexicon-bosworth-toller-lineage.md"
  - "sources/crist-2011-dictionary-processing.md"
summary: "Bosworth-Toller builds need separate checks for transcription, entry structure, and lexical interpretation; common digital ancestry limits corroboration."
provenance:
  extracted: 0.2
  inferred: 0.7
  ambiguous: 0.1
base_confidence: 0.5
lifecycle: draft
lifecycle_changed: "2026-10-28"
tier: supporting
created: 2026-10-28T17:28:59+00:00
updated: 2026-10-28T17:40:07+00:00
---

# Bosworth-Toller × Dictionary build

## The Connection

[[entities/bosworth-toller]] becomes a different research instrument when [[projects/wyrdcraeft/concepts/dictionary-build]] turns printed entries into searchable senses and links to generated forms. External research supports a more precise conclusion than “shared data is weak evidence”: each transformation creates a different claim to verify. ^[inferred]

## Where They Co-occur

The original scan found five shared backlinks. [[references/btc-anglo-saxon]] and [[references/oe-dictionary-repos]] compare derivatives; [[projects/wyrdcraeft/wyrdcraeft]], [[projects/wyrdcraeft/concepts/source-conversion]], and [[projects/wyrdcraeft/concepts/dictionary-query-and-browse]] locate the build among its consumers.

## External Evidence

The Germanic Lexicon Project documents OCR followed by automated and volunteer correction. Its July 2020 notice identifies the Charles University continuation as a better-corrected successor. The historical record therefore establishes a shared digital ancestry with subsequent revision, rather than interchangeable copies. See [[sources/germanic-lexicon-bosworth-toller-lineage]].

Crist’s dictionary-processing draft separates acquisition, tagging, parsing, and validation. Its field-level checks include character and abbreviation inventories, numbering, and external comparisons. These tests serve different purposes from checking a dictionary’s lexical interpretation. See [[sources/crist-2011-dictionary-processing]], §§3.3.2 and 3.3.8.

## Cross-cutting Insight

Three questions should remain separately answerable: did the transcription preserve the printed evidence; did the parser assign its structure correctly; and is the dictionary’s analysis persuasive for the passage being read? Agreement between parsers over one input can help with the second question. It cannot independently settle the first or third. ^[inferred]

The existing build retains raw sense labels, distinct homograph blocks, and unresolved form links. Those documented choices make a useful starting point for tracing decisions. A normalized search key can then broaden access without being treated as an assertion that every matched spelling or entry is equivalent. ^[inferred]

## Tensions and Trade-offs

A corrected descendant may be more accurate than its ancestor while remaining dependent on it. Conversely, restoring the exact printed wording can preserve a lexicographic error. Fidelity and correction are separate deliverables. ^[inferred]

Corpus absence should trigger inspection rather than automatic deletion of a rare form. Generated paradigms are predictions, not new attestations. These distinctions matter when dictionary data supplies both a generator’s input and its apparent test oracle. ^[inferred]

## Strongest Objection

Lineage tracing adds little if the actual task is merely reproducible conversion of a known source. Parser agreement is legitimate evidence for that limited task. The demand for independent lexical corroboration should be tied to a lexical claim, not imposed on every conversion.

> test: for a sample stratified by homographs, nested senses, and rare forms, which disagreements arise in transcription, structure, or interpretation, and can each be resolved with the appropriate witness?

## Open Questions

- Which entries expose the sibling-merge step’s most consequential distinctions when checked against page images and an independently edited lexical source?

## Related

- [[entities/bosworth-toller]]
- [[projects/wyrdcraeft/concepts/dictionary-build]]
- [[synthesis/ocr-character-inventory-x-regreek]]

## Sources

- [[sources/germanic-lexicon-bosworth-toller-lineage]] — project’s own digitization history
- [[sources/crist-2011-dictionary-processing]] — unpublished methodological draft; not a wyrdcraeft evaluation
- [[projects/wyrdcraeft/concepts/dictionary-build]] — existing documented behaviour
- [[references/btc-anglo-saxon]]
- [[references/oe-dictionary-repos]]
