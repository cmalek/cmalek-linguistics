---
title: >-
    Wright catalog
category: concepts
tags: [old-english, morphology, python, wyrdcraeft]
relationships:
  - target: "[[projects/wyrdcraeft/wyrdcraeft]]"
    type: part_of
  - target: "[[concepts/old-english-grammar]]"
    type: related_to
  - target: "[[projects/wyrdcraeft/concepts/morphology-generation]]"
    type: part_of
  - target: "[[projects/wyrdcraeft/concepts/dictionary-query-and-browse]]"
    type: supports
sources:
  - "repo:github.com/cmalek/wyrdcraeft"
summary: >-
    Wright classes seed during morphology generation. Section prose and the legacy Wright audit are separate dictionary commands.
provenance:
  extracted: 0.85
  inferred: 0.10
  ambiguous: 0.05
base_confidence: 0.59
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T16:50:00Z
updated: 2026-10-09T16:50:00Z
---

# Wright catalog

The catalog is reference data inside the same SQLite file as dictionary entries and generated forms. Canonical class assignment lives in `lemma_morph_classes`, keyed by normalized title and part of speech. The legacy `wright` field on source rows is audit input only.

`wright_paradigms.json` supplies morph classes, Wright section links, and bibliographic sources. Build seeds that fixture when catalog tables are empty. `--refresh-catalog` forces a reload. Paragraph text is not part of that seed.

Assignment priority, before form generation: paradigm or verb `paraID`, then part-of-speech features, then intersection with Wright sections at §330 or above. If none of those hit, the lemma gets no assignment row.

## Three processes

```mermaid
flowchart TD
    fixture[wright_paradigms.json] --> seed[Seed during morphology generation]
    seed --> classes[(morph classes and lemma assignments)]

    md[Wright markdown] --> ingest[dictionary ingest-wright-text]
    ingest --> prose[(section_text on wright_sections)]
    prose --> browse[Browse modal]

    source[Legacy wright fields on source rows] --> audit[dictionary audit-wright]
    classes --> audit
    audit --> report[Report only: malformed, contradiction, unclassified, blank-but-classified]
```

`wyrdcraeft dictionary ingest-wright-text --source PATH` parses `§ N` headings and fills empty `section_text` cells. `--force` overwrites. It reports markdown sections missing from the catalog, catalog sections still empty, and a coverage percent. The bundled `wright.md` currently has phonology §1–58 only, so inflection citations at §330 and above show an ingest-needed message until a fuller markdown file is ingested.

`wyrdcraeft dictionary audit-wright` compares legacy source `wright` values with the assigned classes. Categories are malformed legacy Wright, contradiction against the assigned section, unclassified lemma plus part of speech, and blank legacy field on a classified lemma. Version 1 does not rewrite sources and exits 0. `--json` prints the full result.

`docs/context/morphology.md` still names `morphology ingest-wright-text` and `morphology audit-wright`. The live commands are on `dictionary`.
