---
title: >-
    Verify a Plan in a Throwaway Worktree
category: skills
tags: [git, testing, workflow, python]
relationships:
  - target: "[[skills/claude-code-builtin-cd]]"
    type: uses
  - target: "[[projects/wyrdcraeft/wyrdcraeft]]"
    type: related_to
sources:
  - "agent:wyrdcraeft-session-2026-10-08"
summary: >-
    Extract a plan’s code into a detached git worktree and run its tests, ruff, and mypy so wrong expectations show up before execution.
provenance:
  extracted: 0.85
  inferred: 0.15
  ambiguous: 0.00
base_confidence: 0.42
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T15:54:00Z
updated: 2026-10-09T15:54:00Z
snapshots:
  - "[[_raw/_archived/2026-10-08-verify-plan-code-in-throwaway-git-worktree|2026-10-08-verify-plan-code-in-throwaway-git-worktree]]"
---

# Verify a Plan in a Throwaway Worktree

Before handing an implementation plan over, run **the plan’s own code** in a throwaway tree. Reading the plan missed wrong test expectations and lint that showed up once the fences were executed.

## Key Ideas

- Create `git worktree add --detach <scratch>/wt HEAD`. Parse fenced code per `### Task N:` section, write those blocks to the paths the steps name, then run the plan’s tests, `ruff check`, `mypy`, and a dry run on real data.
- On [[projects/wyrdcraeft/wyrdcraeft]], that pass found a caron typed instead of a breve, a normalized key that kept `æ`, a wrong gate-threshold table, and lint (E741, E501, FLY002, PT019, ARG001).
- 281 importer-plan tests passed against the plan’s code; the dry run matched prototype counts.
- The project is installed editable from the **main** checkout. Set `PYTHONPATH` to the worktree and make that directory the cwd (see [[skills/claude-code-builtin-cd]]); confirm with `print(pkg.__file__)`.
- Remove with `git worktree remove --force`. Keep prototype scripts in the scratchpad, not the repo.

## Open Questions

- Whether the Task-N regex generalizes beyond the importer plan’s heading style. ^[inferred]

## Sources

- [[_raw/_archived/2026-10-08-verify-plan-code-in-throwaway-git-worktree.md]]
