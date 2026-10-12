---
title: >-
    Source conversion
category: concepts
tags: [old-english, python, wyrdcraeft]
relationships:
  - target: "[[projects/wyrdcraeft/wyrdcraeft]]"
    type: part_of
  - target: "[[projects/wyrdcraeft/concepts/diacritic-workflows]]"
    type: related_to
  - target: "[[skills/linguistic-pdf-to-markdown]]"
    type: related_to
sources:
  - "repo:github.com/cmalek/wyrdcraeft"
summary: >-
    source convert turns a local TEI/XML or text file into one JSON document. It does not fetch URLs or call a model.
provenance:
  extracted: 0.90
  inferred: 0.08
  ambiguous: 0.02
base_confidence: 0.59
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T16:50:00Z
updated: 2026-10-09T18:20:00Z
---

# Source conversion

`wyrdcraeft source convert <source> <output>` reads a local file that already exists and writes one JSON document to the path you give. An optional `--title` overrides the title. The command does not download anything and does not call a language model. That work left this repo with the OCR and messy-document pipeline. How to get a faithful markdown or TEI file out of a linguistic PDF, before this command sees it, is [[skills/linguistic-pdf-to-markdown]].

## Flow

```mermaid
flowchart TD
    cmd[source convert] --> exists{Local file exists}
    exists -->|no| stop[Fail before conversion]
    exists -->|yes| suffix{Suffix}
    suffix -->|".tei or .xml"| tei[TEI ingest]
    suffix -->|other, including .txt| heur[Heuristic text ingest]
    tei --> model[Old English text model]
    heur --> model
    model --> json[Write JSON to the given output path]
```

TEI and XML go through the TEI ingestor. Everything else, including `.txt`, goes through the heuristic ingestor. Shared ingest behavior belongs on the general entrypoint, not on one caller.

This path is separate from dictionary indexing. [[entities/bosworth-toller]] source text is built by [[projects/wyrdcraeft/concepts/dictionary-build]], not by `source convert`.
