---
title: >-
    Rebase a Long-Diverged Refactor
category: skills
tags: [git, testing, workflow]
relationships:
  - target: "[[projects/aenglisc-toolkit/aenglisc-toolkit]]"
    type: related_to
sources:
  - "agent:aenglisc-toolkit-session-2026-10-02"
summary: >-
    Replaying many commits onto a parallel refactor re-conflicts per commit; squash, rebase once, then test — clean auto-merges can still be semantically broken.
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
  - "[[_raw/_archived/2026-10-02-git-squash-rebase-diverged-refactor|2026-10-02-git-squash-rebase-diverged-refactor]]"
---

# Rebase a Long-Diverged Refactor

An 18-commit refactor on [[projects/aenglisc-toolkit/aenglisc-toolkit]] sat 48 commits behind master, which had refactored the same area.

## Key Ideas

**Squash first.** `git rebase master` conflicted on the first of 18 commits (7 hunks in 2 files). Both sides had independently created 9 of the same files (add/add), so those files would re-conflict every commit. Parallel refactors make conflicts semantic; replaying history multiplies the work.

Check overlap with `comm -12` of `git diff --name-only $(git merge-base master HEAD) master` against the same for `HEAD`, and `--diff-filter=A` for add/add files. Backup branch, `git reset --soft $(git merge-base master HEAD)`, commit once, then `git rebase master` for a single resolution. `git rebase --abort` is safe if a rebase already started.

Confirmed: single-pass rebase finished; `git diff backup HEAD` empty (tree identical to the backup before rebasing).

**Untracked files that master also tracks block the rebase.** `git stash push -u` first. After the rebase, restore only files that differ from master from saved copies — not `git stash pop`, which collides with now-tracked paths.

**Bulk-resolving trivial hunks.** In a rebase, “ours” is the branch being rebased **onto** (master) and “theirs” is your commit. A tiny script that picks one side of every hunk is enough when hunks are doc-comment-only. Take master’s side for generated files and lockfiles, then regenerate (`uv lock`, graph, help build).

**Clean auto-merges can be semantically broken.** After every conflict was resolved, the first test failed: `tests/conftest.py` had two QSettings isolation setups (master’s session fixture and the branch’s module-level redirect) pointing at different temp dirs, and one branch test constructed `SentenceCard` without the `command_manager` master now requires. Neither conflicted textually. Fix: session fixture reuses the module-level dir; pass `command_manager=CommandManager(db_session)`. Full suite then 1012 passed, 1 skipped.

`uv lock` after the merge removed 4 deps the branch had dropped; grep that nothing still imports them before keeping the regenerated lock.

## Open Questions

- Whether the same squash-then-rebase rule applies when history must be preserved for review rather than landed as one commit. ^[inferred]

## Sources

- [[_raw/_archived/2026-10-02-git-squash-rebase-diverged-refactor.md]]
