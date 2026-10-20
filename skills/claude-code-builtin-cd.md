---
title: >-
    Claude Code Bash: Use builtin cd
category: skills
tags: [shell, tooling, git, workflow]
relationships:
  - target: "[[skills/verify-plan-in-throwaway-worktree]]"
    type: related_to
  - target: "[[projects/wyrdcraeft/wyrdcraeft]]"
    type: related_to
sources:
  - "agent:wyrdcraeft-session-2026-10-08"
summary: >-
    In one Claude Code snapshot, cd into long scratch paths printed chdir: command not found and stopped && chains; builtin cd avoids silent wrong-cwd runs.
provenance:
  extracted: 0.75
  inferred: 0.25
  ambiguous: 0.00
base_confidence: 0.42
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T15:54:00Z
updated: 2026-10-18T21:00:00Z
snapshots:
  - "[[_raw/_archived/2026-10-08-claude-code-bash-cd-fails-use-builtin-cd|2026-10-08-claude-code-bash-cd-fails-use-builtin-cd]]"
  - "[[_raw/_archived/2026-10-18-agent-shell-quirks-cd-grep-context7|2026-10-18-agent-shell-quirks-cd-grep-context7]]"
---

# Claude Code Bash: Use builtin cd

A [[skills/verify-plan-in-throwaway-worktree]] run on [[projects/wyrdcraeft/wyrdcraeft]] failed because the shell never entered the worktree.

## Key Ideas

- `git worktree add … && cd $WT && python3 script.py` printed `chdir: command not found`. The `&&` chain stopped; a later unchained line still ran in the **old** directory. `python -m pytest` then imported the editable package from the main checkout.
- The sourced snapshot wraps `cd`; that wrapper called a missing `chdir`. Plain `cd` to the repo root usually worked; `cd` to a long scratch path did not. Cause inferred, not isolated. ^[inferred]
- Use `builtin cd`, or `os.chdir` inside Python, or absolute paths. Check `pwd` before anything that writes relative paths.

```bash
# ❌ cd $WT && python -m pytest ...
# ✅ builtin cd $WT && PYTHONPATH=$WT python -m pytest ...
```

- Confirmed: `pwd` and `wyrdcraeft.__file__` pointed at the worktree after `builtin cd`.

## Second sighting: `/usr/bin/cd` is not a substitute

On 2026-10-18 the aenglisc_toolkit repo's `AGENTS.md` said to "always use `/usr/bin/cd`; bare `cd` is a bash function and breaks agent shells", and the user repeated it mid-session. The same `chdir: command not found` appeared from the snapshot, and `type cd` reported `cd is a function`.

- `/usr/bin/cd` is a separate process, so it exits 0 and changes nothing. `/usr/bin/cd dir && cat file` ran in the old directory and failed with "No such file".
- `builtin cd dir && pwd` did enter the directory, within that one Bash call.
- Absolute paths avoid both problems, so they are the safest default.

## Open Questions

- Whether this wrapper exists in every Claude Code shell snapshot or only some hosts. It has now appeared in two sessions (wyrdcraeft and aenglisc_toolkit work); whether they share a host is unknown. ^[ambiguous]
- The `AGENTS.md` rule predates this finding and could be changed to `builtin cd` or absolute paths. ^[inferred]

## Sources

- [[_raw/_archived/2026-10-08-claude-code-bash-cd-fails-use-builtin-cd.md]]
- [[_raw/_archived/2026-10-18-agent-shell-quirks-cd-grep-context7.md]]
