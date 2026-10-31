---
title: "Glob URL cache: char-wise common prefix can contain a wildcard and never match"
category: skills
tags:
  - topic/python
  - routing
  - glob
  - debugging
summary: "commonprefix over multiple glob paths can yield a prefix containing '*', which startswith() lookups never match; cut the prefix at the first '*'."
tier: supporting
related: []
extends: null
contradicts: null
superseded_by: null
capture_source: claude-session
project: "access.caltech-proxy"
base_confidence: 0.85
lifecycle: draft
lifecycle_changed: 2026-10-21
provenance:
  extracted: 0.9
  inferred: 0.1
sources:
  - "access.caltech-proxy session (2026-10-21)"
---

## Glob cache prefix containing `*` makes an app unroutable

**Problem:** An app with several `CAPAuthorizationURL` globs (`/hd/sync/mappings/*/`, `.../*/delete/`, `.../*/enable/`) registered fine, with a log line showing `prefix=/hd/sync/mappings/*/`. Requests to `/hd/sync/mappings/1/` then returned 403, and `acproxy users permitted` printed "No app owns ...".

**Root cause:** `GlobCAPAuthorizationURLApplicationCache.add` computed the prefix with `os.path.commonprefix(glob_paths)`, which compares characters and does not stop at wildcards. `get()` finds candidate prefixes with `path.startswith(prefix)`. A real path never starts with a literal `*`, so the entry could never be found. The single-glob branch already cut at the first `*`, so only apps with two or more globs were affected. The code was the same before and after the cache package refactor (`83c2f33`), so the bug appeared when the config gained the multi-glob shape.

**Fix:**
```python
# ❌ before
prefix = os.path.commonprefix(glob_paths)
# ✅ after
prefix = os.path.commonprefix(glob_paths).split("*")[0]
```

**Confirmed by:** a regression test that failed before the fix and passed after; a manual mutant (removing the `.split`) was killed by the test; full suite passes apart from unrelated WIP in `acproxy/cli/users.py`.

**Notes:** The char-wise prefix can still end mid-segment (`/foo/ba` for `/foo/bar/*` + `/foo/baz/*`). That only widens the match, so lookups still work. `acproxy users permitted` queries only the `authorized_url` index, so it may still miss glob-only paths; this was not checked against `HEAD`.
