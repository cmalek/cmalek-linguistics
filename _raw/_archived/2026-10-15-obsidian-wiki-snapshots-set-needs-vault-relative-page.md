---
title: "obsidian-wiki snapshots set: page must be vault-relative, pass --vault"
category: skills
tags:
  - topic/obsidian-wiki
  - tooling
summary: "`obsidian-wiki snapshots set` fails with 'page not found' when given an absolute page path; give a vault-relative page plus --vault."
tier: supporting
capture_source: claude-session
base_confidence: 0.7
lifecycle: draft
lifecycle_changed: 2026-10-15
provenance:
  extracted: 0.9
  inferred: 0.1
sources:
  - "agent:wiki-ingest-session-2026-10-15"
---

# obsidian-wiki snapshots set: page must be vault-relative

**Problem:** `obsidian-wiki snapshots set /abs/path/vault/skills/page.md --archive "_raw/_archived/x.md"` printed `error: page not found`, although the file existed.

**Cause:** the `page` argument is documented as "vault-relative wiki page", and the vault is resolved from config unless `--vault` is given. An absolute path is not accepted.

**Fix:** `obsidian-wiki snapshots set skills/page.md --archive "_raw/_archived/x.md" --vault /abs/path/vault`. `cache-update` accepts absolute source paths and normalises them to vault-relative keys, so only `snapshots set` is strict.

**Order:** run `snapshots set` after the raw file is moved into `_raw/_archived/`, then `cache-update` on the archived path.
