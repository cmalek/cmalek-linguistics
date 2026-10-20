---
title: >-
  obsidian-wiki snapshots set needs a vault-relative page
category: skills
tags: [obsidian-wiki, tooling, ingest]
sources:
  - "agent:wiki-ingest-session-2026-10-15"
relationships:
  - target: "[[skills/webfetch-pdf-to-pdftotext]]"
    type: related_to
  - target: "[[skills/claude-code-builtin-cd]]"
    type: related_to
summary: >-
  `obsidian-wiki snapshots set` rejects an absolute page path with "page not found"; pass a vault-relative page and --vault.
provenance:
  extracted: 0.9
  inferred: 0.1
  ambiguous: 0.0
base_confidence: 0.6
lifecycle: draft
lifecycle_changed: "2026-10-17"
tier: supporting
created: 2026-10-17T18:40:00Z
updated: 2026-10-17T18:40:00Z
snapshots:
  - "[[_raw/_archived/2026-10-15-obsidian-wiki-snapshots-set-needs-vault-relative-page|2026-10-15-obsidian-wiki-snapshots-set-needs-vault-relative-page]]"
---

# obsidian-wiki snapshots set needs a vault-relative page

`obsidian-wiki snapshots set /abs/path/vault/skills/page.md --archive "_raw/_archived/x.md"` prints `error: page not found` even though the file exists. The `page` argument is documented as a vault-relative wiki page, and the vault comes from config unless `--vault` is given.

## Fix

```bash
obsidian-wiki snapshots set skills/page.md \
  --archive "_raw/_archived/x.md" --vault /abs/path/vault
```

`cache-update` accepts absolute source paths and normalises them to vault-relative keys, so only `snapshots set` is strict.

## Order

1. Move the raw file into `_raw/_archived/`.
2. `snapshots set` on the page, pointing at the archived path.
3. `cache-update` on the archived path.

## Sources

- [[_raw/_archived/2026-10-15-obsidian-wiki-snapshots-set-needs-vault-relative-page|2026-10-15-obsidian-wiki-snapshots-set-needs-vault-relative-page]]
