---
title: >-
    Dictionary query and browse
category: concepts
tags: [old-english, lexicography, python, wyrdcraeft]
relationships:
  - target: "[[projects/wyrdcraeft/wyrdcraeft]]"
    type: part_of
  - target: "[[entities/bosworth-toller]]"
    type: uses
  - target: "[[projects/wyrdcraeft/concepts/dictionary-build]]"
    type: depends_on
  - target: "[[projects/wyrdcraeft/concepts/morphology-generation]]"
    type: depends_on
  - target: "[[projects/wyrdcraeft/concepts/wright-catalog]]"
    type: uses
sources:
  - "repo:github.com/cmalek/wyrdcraeft"
summary: >-
    Query prints Bosworth-Toller entries from a populated index. Browse is a read-only shell with search, senses, and a morphology sidebar.
provenance:
  extracted: 0.80
  inferred: 0.15
  ambiguous: 0.05
base_confidence: 0.59
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T16:50:00Z
updated: 2026-10-09T16:50:00Z
---

# Dictionary query and browse

Both commands read canonical `wyrdcraeft.sqlite3`. Neither writes dictionary or morphology rows. Rebuild with [[projects/wyrdcraeft/concepts/dictionary-build]] after source changes.

## Query

`wyrdcraeft dictionary query` looks up a lemma or variant spelling, with an optional part-of-speech filter. Output is text or JSON.

The command refuses to run unless `bt_entries`, `bt_senses`, and `bt_variants` are populated. A migrated but empty database is expected until build has run. The hidden `dictionary lookup` command is the same lookup with a deprecation warning.

```mermaid
flowchart TD
    query[dictionary query] --> file{Canonical DB exists}
    file -->|no| missing[Fail: database missing]
    file -->|yes| tables{bt_entries, bt_senses, bt_variants populated}
    tables -->|no| empty[Fail: run dictionary build]
    tables -->|yes| lookup[Normalize the lemma and look up entries]
    lookup --> render{JSON flag}
    render -->|yes| json[JSON array]
    render -->|no| text[Formatted entry text]
```

## Browse

`wyrdcraeft dictionary browse` opens a Textual shell. The search bar is at the top. Results sit on the left. Details and part-of-speech-filtered paradigm grids share the right column. Search accepts æ, þ, ð, macrons, and dotted letters from the keyboard when the field is focused. A character bar under the field covers terminals that cannot emit those keys.

Results sort by rank tier, then by lexical distance from the query. The project context describes that ranking as a 12-tier search.

The morphology sidebar shows forms for the headword’s part of speech and builds grids from inflection codes. Detail text includes the catalog morph class, its provenance, and a selectable Wright section list, or an explicit Unclassified state. Choosing a section opens stored paragraph text, or a message that [[projects/wyrdcraeft/concepts/wright-catalog|Wright ingest]] is still needed.

Browse is read-only. It does not parse Wright markdown at view time.
