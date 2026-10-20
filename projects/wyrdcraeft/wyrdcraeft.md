---
title: >-
    wyrdcraeft
category: project
tags: [old-english, morphology, python, dictionary]
relationships:
  - target: "[[concepts/old-english]]"
    type: related_to
  - target: "[[concepts/old-english-grammar]]"
    type: related_to
  - target: "[[concepts/oe-word-formation]]"
    type: related_to
  - target: "[[entities/bosworth-toller]]"
    type: uses
  - target: "[[projects/wyrdcraeft/concepts/startup-and-settings]]"
    type: contains
  - target: "[[projects/wyrdcraeft/concepts/source-conversion]]"
    type: contains
  - target: "[[projects/wyrdcraeft/concepts/diacritic-workflows]]"
    type: contains
  - target: "[[projects/wyrdcraeft/concepts/dictionary-build]]"
    type: contains
  - target: "[[projects/wyrdcraeft/concepts/morphology-generation]]"
    type: contains
  - target: "[[projects/wyrdcraeft/concepts/dictionary-query-and-browse]]"
    type: contains
  - target: "[[projects/wyrdcraeft/concepts/wright-catalog]]"
    type: contains
  - target: "[[skills/verify-plan-in-throwaway-worktree]]"
    type: uses
sources:
  - "repo:github.com/cmalek/wyrdcraeft"
  - "agent:wyrdcraeft-session-2026-10-08"
summary: >-
    Process map for the Old English toolkit: conversion, diacritics, dictionary build, morphology, browse, and Wright catalog. Not a symbol index.
provenance:
  extracted: 0.75
  inferred: 0.20
  ambiguous: 0.05
base_confidence: 0.59
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T15:54:00Z
updated: 2026-10-09T16:50:00Z
snapshots:
  - "[[_raw/_archived/2026-10-08-verify-plan-code-in-throwaway-git-worktree|2026-10-08-verify-plan-code-in-throwaway-git-worktree]]"
  - "[[_raw/_archived/2026-10-08-claude-code-bash-cd-fails-use-builtin-cd|2026-10-08-claude-code-bash-cd-fails-use-builtin-cd]]"
  - "[[_raw/_archived/2026-10-08-click-clirunner-rich-stderr-console-not-captured|2026-10-08-click-clirunner-rich-stderr-console-not-captured]]"
---

# wyrdcraeft

`wyrdcraeft` is a local Python CLI for [[concepts/old-english]] text. It converts source files, restores diacritics, builds a [[entities/bosworth-toller]] index, generates inflected forms, and browses dictionary entries beside those forms. One canonical SQLite file, `wyrdcraeft.sqlite3`, holds dictionary tables, morphology `forms`, and the Wright morph catalog.

These pages describe processes. They do not list internal symbols.

## How the processes fit

```mermaid
flowchart TD
    start[Every CLI command] --> settings[Load settings]
    settings --> ready[Database readiness gate, morphology and dictionary only]
    ready --> work{Which command}

    work --> convert[source convert]
    work --> marks[source mark-diacritics]
    work --> diacritic[diacritic curation]
    work --> build[dictionary build]
    work --> query[dictionary query]
    work --> browse[dictionary browse]
    work --> wright[Wright ingest or audit]
    work --> morphq[morphology query]

    convert --> json[Document JSON]
    marks --> text[Marked text plus reports]
    diacritic --> index[Macron index JSON]
    build --> db[(wyrdcraeft.sqlite3)]
    build --> morph[Morphology generation when forms are empty or forced]
    morph --> db
    query --> db
    browse --> db
    wright --> db
    morphq --> db
```

## Processes

- [[projects/wyrdcraeft/concepts/startup-and-settings]] — settings load and the Alembic readiness gate that runs before database commands.
- [[projects/wyrdcraeft/concepts/source-conversion]] — local `.txt` or TEI/XML into document JSON. No fetch and no LLM.
- [[projects/wyrdcraeft/concepts/diacritic-workflows]] — additive macron transfer, and curation of the macron index.
- [[projects/wyrdcraeft/concepts/dictionary-build]] — parse Bosworth-Toller, write `bt_*`, relink forms, regenerate morphology when needed.
- [[projects/wyrdcraeft/concepts/morphology-generation]] — paradigm assignment, Wright class assignment, then form stages into SQLite.
- [[projects/wyrdcraeft/concepts/dictionary-query-and-browse]] — lemma lookup, and the read-only Textual browse shell.
- [[projects/wyrdcraeft/concepts/wright-catalog]] — seed classes during build; ingest section prose and audit legacy Wright fields separately.

## Out of this repo

OCR, LLM ingest, and messy-document conversion live in `wordwending` (formerly `bochord`). ^[extracted]

## Session notes

Notes from 2026-10-08 cover how plans and CLI tests were checked. They do not describe the linguistic model.

- [[skills/verify-plan-in-throwaway-worktree]] — run a plan’s own code in a detached worktree before executing it on the main tree.
- [[skills/claude-code-builtin-cd]] — `builtin cd` so pytest imports the worktree package, not the editable main checkout.
- [[skills/click-clirunner-rich-stderr]] — CliRunner misses Rich stderr consoles bound at import; monkeypatch the print helper.

## Related

- [[concepts/old-english-grammar]] — the inflectional system the generator is written against.
- [[concepts/oe-word-formation]] — affix and compound patterns beside the generator, not a description of it. ^[inferred]
- [[projects/aenglisc-toolkit/aenglisc-toolkit]] — neighbouring OE reading app; Qt, not this CLI.
