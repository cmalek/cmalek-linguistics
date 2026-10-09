---
title: "Claude Code Bash tool: cd can fail with 'chdir: command not found'"
category: skills
tags:
  - topic/claude-code
  - shell
  - tooling
summary: "In one Claude Code shell snapshot, cd into some paths printed 'chdir: command not found' and short-circuited && chains; builtin cd and absolute paths avoid silent wrong-cwd runs."
tier: supporting
related: []
extends: null
contradicts: null
superseded_by: null
capture_source: claude-session
project: "wyrdcraeft"
base_confidence: 0.75
lifecycle: draft
lifecycle_changed: 2026-10-08
provenance:
  extracted: 0.8
  inferred: 0.2
sources:
  - "wyrdcraeft session (2026-10-08)"
---

## `cd` failed silently in a command chain

**Problem:** `git worktree add ... && cd $WT && python3 script.py` printed `chdir: command not found` from the shell snapshot. The `&&` chain stopped, so the script never ran, while a later unchained line still ran in the old directory. `python -m pytest` then imported the package from the main checkout instead of the worktree.

**Root cause:** The sourced shell snapshot wraps `cd` and the wrapper called a missing `chdir`. Plain `cd` to the repo root usually worked; `cd` to a long scratch path did not. (Cause inferred, not isolated.) ^[inferred]

**Fix:**

```bash
# ❌ cd $WT && python -m pytest ...
# ✅ builtin cd $WT && PYTHONPATH=$WT python -m pytest ...
```

Use `builtin cd`, or `os.chdir` inside a Python script, or absolute paths. Check `pwd` before running anything that writes relative paths.

**Confirmed by:** `pwd` and `wyrdcraeft.__file__` showed the worktree after switching to `builtin cd`.
