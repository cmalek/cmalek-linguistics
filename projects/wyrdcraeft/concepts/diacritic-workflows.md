---
title: >-
    Diacritic workflows
category: concepts
tags: [old-english, python, wyrdcraeft]
relationships:
  - target: "[[projects/wyrdcraeft/wyrdcraeft]]"
    type: part_of
  - target: "[[projects/wyrdcraeft/concepts/source-conversion]]"
    type: related_to
  - target: "[[entities/bosworth-toller]]"
    type: uses
  - target: "[[skills/linguistic-pdf-to-markdown]]"
    type: related_to
sources:
  - "repo:github.com/cmalek/wyrdcraeft"
summary: >-
    Two related jobs: mark macrons onto a text without changing existing letters, and curate the macron index those marks come from.
provenance:
  extracted: 0.85
  inferred: 0.10
  ambiguous: 0.05
base_confidence: 0.59
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T16:50:00Z
updated: 2026-10-09T18:20:00Z
---

# Diacritic workflows

Restoration consumes the macron index. Curation changes it. They share packaged data under `wyrdcraeft/etc/diacritic/`, including the default index `oe_bt_macron_index.json` and hand-edited palatalization lists.

Normalized keys are lowercased, diacritics are stripped, and `ð` becomes `þ`.

This pass adds marks to a text that lacks them. It is not a substitute for copying an edition that already prints macrons and dots. If PDF extraction drops those marks, this command has to guess them back. [[skills/linguistic-pdf-to-markdown]] is the step that tries to keep the printed marks.

## Mark a text

`wyrdcraeft source mark-diacritics` adds macrons and dot diacritics. It does not alter characters already in the file. A key whose options all share one mark pattern is applied like a unique entry unless that key is completed. Other ambiguous keys follow `--ambiguity-policy` (`auto`, `leave`, or `union`). Completed keys are never guessed. Reports cover unaligned tokens, ambiguity, and unknown words.

Standard elements from `standard_elements.txt` are spelled as listed before transfer. They count only where Bosworth-Toller writes a hyphen after a prefix or around a compound, so `ge-an` and `gēan` stay apart.

## Curate the index

| Command | What it does |
|---|---|
| `diacritic add` | Insert a unique normalized/macron pair. Refuses ambiguous keys. Refuses an existing unique key unless `--force`. |
| `diacritic delete` | Remove a unique pair. |
| `diacritic import-variants` | Add Bosworth-Toller variants as their own unique entries. Dry run unless `--apply`. Never changes an existing key. |
| `diacritic disambiguate` | Interactive resolution of ambiguous entries. `q` leaves the session immediately. |

`CONTEXT.md` still names a hyphenated `diacritic-disambiguate` command. The registered command is `wyrdcraeft diacritic disambiguate`.

```mermaid
flowchart TD
    index[(Macron index)] --> mark[source mark-diacritics]
    text[Source text] --> mark
    mark --> out[Restored text]
    mark --> reports[Unaligned, ambiguity, and unknown reports]

    add[diacritic add] --> index
    delete[diacritic delete] --> index
    variants[diacritic import-variants] --> review{Existing key, conflict, or below gate}
    review -->|yes| report[Review report, index unchanged for that key]
    review -->|no, and --apply| index
    disambiguate[diacritic disambiguate] --> index
```

`diacritic add` will not overwrite an ambiguous entry. Those keys go through disambiguation. The disambiguation queue skips a key whose options already collapse to one mark pattern; naming that key still opens it.
