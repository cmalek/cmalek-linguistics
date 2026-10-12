---
title: >-
    Dictionary build
category: concepts
tags: [old-english, lexicography, python, wyrdcraeft]
relationships:
  - target: "[[projects/wyrdcraeft/wyrdcraeft]]"
    type: part_of
  - target: "[[entities/bosworth-toller]]"
    type: uses
  - target: "[[projects/wyrdcraeft/concepts/morphology-generation]]"
    type: triggers
  - target: "[[projects/wyrdcraeft/concepts/dictionary-query-and-browse]]"
    type: precedes
  - target: "[[projects/wyrdcraeft/concepts/startup-and-settings]]"
    type: depends_on
sources:
  - "repo:github.com/cmalek/wyrdcraeft"
summary: >-
    dictionary build parses Bosworth-Toller into bt_* tables, relinks morphology forms, and regenerates forms when the table is empty or --with-morphology is set.
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

# Dictionary build

`wyrdcraeft dictionary build` is the unified write path into canonical `wyrdcraeft.sqlite3`. The default source is packaged `wyrdcraeft/etc/dictionary/oe_bt.txt`. `--source` overrides it. Optional outputs are a JSON report and `parse_warnings.jsonl`.

One source block becomes one `bt_entries` row. Homographs that share a normalized key and part of speech stay separate blocks. Sense paths such as `1.2` are internal hierarchy, not the printed Bosworth-Toller labels. Those labels stay in `source_label_raw`.

`dictionary clean-headwords` is a source-file cleanup: it lowercases all-uppercase headwords in `oe_bt.txt` before a later build. `dictionary lookup` still runs, prints a deprecation warning, and forwards to `dictionary query`.

## Flow

```mermaid
flowchart TD
    cmd[dictionary build] --> schema[Upgrade canonical schema]
    schema --> clear[Clear forms.entry_id]
    clear --> read[Read oe_bt.txt line by line]
    read --> parse[Parse and segment senses]
    parse --> warn[Write parse warnings]
    parse --> merge[Merge editorial siblings]
    merge --> write[Write bt_entries, bt_senses, bt_variants, bt_edit_log]
    write --> relink[Relink forms.entry_id]
    relink --> need{forms empty or --with-morphology}
    need -->|yes| require{bt_entries present}
    require -->|no| fail[Stop: morphology needs dictionary rows]
    require -->|yes| wipe[Delete forms]
    wipe --> morph[Morphology generation]
    morph --> relink2[Count links after regeneration]
    need -->|no| infer
    relink2 --> infer[Infer POS when forms exist]
    infer --> report[Build report]
```

Unmatched or ambiguous form joins leave `entry_id` null. The relink step clears every `forms.entry_id` and recomputes it. Unapplied edits whose notes start with `target_missing` or `target_ambiguous` are copied into the warnings file.

Morphology is not a separate product command anymore. Generation runs inside this build when `forms` is empty, or whenever `--with-morphology` is passed. See [[projects/wyrdcraeft/concepts/morphology-generation]].

`docs/context/morphology.md` still lists `morphology build`. The live CLI registers build on `dictionary`.
