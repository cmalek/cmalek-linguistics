---
title: "Verify an implementation plan by running its code in a throwaway worktree"
category: skills
tags:
  - topic/workflow
  - testing
  - planning
summary: "Extract a plan's code blocks into a detached git worktree and run its tests, ruff and mypy; this finds wrong expectations before execution."
tier: supporting
related: []
extends: null
contradicts: null
superseded_by: null
capture_source: claude-session
project: "wyrdcraeft"
base_confidence: 0.85
lifecycle: draft
lifecycle_changed: 2026-10-08
provenance:
  extracted: 0.85
  inferred: 0.15
sources:
  - "wyrdcraeft session (2026-10-08)"
---

## Reviewing a plan by executing it

**Pattern:** Before handing a plan over, create `git worktree add --detach <scratch>/wt HEAD`, parse the plan's fenced code blocks per task (a regex over `### Task N:` sections), write them to the paths the steps name, then run the plan's tests, `ruff check`, `mypy`, and a dry run on real data.

**What it found:** wrong test expectations (a caron typed instead of a breve; a normalized key that kept `æ`; a gate threshold table), lint failures (E741, E501, FLY002, PT019, ARG001), and real numbers for the plan's "expected" lines. Reading the plan alone missed all of these.

**Gotchas:** The project is installed editable from the main checkout, so set `PYTHONPATH=<worktree>` and make the worktree the working directory (see the note on `builtin cd`); verify with `print(pkg.__file__)`. Remove the worktree (`git worktree remove --force`) and keep prototype scripts in the scratchpad, never the repo.

**Confirmed by:** 281 tests of the importer plan passed against the plan's own code, and its dry run reproduced the prototype counts exactly.
