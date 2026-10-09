---
title: "Rebasing a long-diverged refactor branch: squash first, then check auto-merges"
category: skills
tags:
  - topic/git
  - workflow/rebase
  - testing/merge-verification
summary: "Replaying many commits onto a branch that did a parallel refactor re-conflicts per commit; squash then rebase once, and test because clean auto-merges can be semantically broken."
tier: supporting
related: []
extends: null
contradicts: null
superseded_by: null
capture_source: claude-session
project: "aenglisc_toolkit"
base_confidence: 0.85
lifecycle: draft
lifecycle_changed: 2026-10-02
provenance:
  extracted: 0.85
  inferred: 0.15
sources:
  - "aenglisc_toolkit session (2026-10-02)"
---

Findings from rebasing an 18-commit refactor branch (48 commits behind master) onto a master that had done its own overlapping refactor.

## Per-commit rebase re-conflicts; squash first

**Problem:** `git rebase master` conflicted on the very first of 18 commits (7 hunks in 2 files), and both sides had independently created 9 of the same new files (add/add), so the same files would re-conflict commit after commit.

**Explanation:** A parallel refactor makes the conflicts semantic, not textual. Replaying history multiplies the resolution work.

**Workaround / Pattern:** Check scope first with `comm -12` of `git diff --name-only $(git merge-base master HEAD) master` against the same for `HEAD`, and `--diff-filter=A` for add/add files. Make a backup branch, `git reset --soft $(git merge-base master HEAD)`, commit once, then `git rebase master` for a single resolution pass. Aborting a started rebase with `git rebase --abort` is safe.

**Confirmed by:** Single-pass rebase finished; tree identical to the backup branch before rebasing (`git diff backup HEAD` empty).

## Untracked files that master also tracks block the rebase

**Behavior:** Untracked copies of files that master tracks make the rebase refuse to run.

**Workaround / Pattern:** `git stash push -u` first. After the rebase, restore only the files that differ from master from saved copies instead of `git stash pop`, which collides with the now-tracked paths.

## Bulk-resolving trivial hunks

**Pattern:** In a rebase, "ours" is the branch being rebased onto (master) and "theirs" is your commit. A tiny script that picks one side of every conflict hunk is enough when the hunks are doc-comment-only. Take master's side for generated files and lockfiles, then regenerate (`uv lock`, graph, help build) instead of hand-merging.

## Clean auto-merges can be semantically broken

**Problem:** After resolving every conflict, the first test failed: `tests/conftest.py` had two QSettings isolation setups (master's session fixture and the branch's module-level redirect) pointing at different temp dirs, and one branch test constructed `SentenceCard` without the `command_manager` that master now requires. Neither conflicted textually.

**Fix:** Make the session fixture reuse the module-level dir; pass `command_manager=CommandManager(db_session)` in the test.

**Confirmed by:** Full suite 1012 passed, 1 skipped after the two fixes.

**Notes:** `uv lock` after the merge removed 4 deps the branch had intentionally dropped; verify with grep that nothing imports them before keeping the regenerated lock.
