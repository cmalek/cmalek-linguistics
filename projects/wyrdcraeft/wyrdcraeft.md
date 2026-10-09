---
title: >-
    wyrdcraeft
category: project
tags: [old-english, morphology, python, testing]
relationships:
  - target: "[[concepts/old-english]]"
    type: related_to
  - target: "[[concepts/oe-word-formation]]"
    type: related_to
  - target: "[[skills/verify-plan-in-throwaway-worktree]]"
    type: uses
sources:
  - "agent:wyrdcraeft-session-2026-10-08"
summary: >-
    Local Old English morphology generator; 2026-10-08 sessions distilled worktree plan checks, Claude Code cd, and Click/Rich CLI tests.
provenance:
  extracted: 0.70
  inferred: 0.25
  ambiguous: 0.05
base_confidence: 0.42
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T15:54:00Z
updated: 2026-10-09T15:54:00Z
snapshots:
  - "[[_raw/_archived/2026-10-08-verify-plan-code-in-throwaway-git-worktree|2026-10-08-verify-plan-code-in-throwaway-git-worktree]]"
  - "[[_raw/_archived/2026-10-08-claude-code-bash-cd-fails-use-builtin-cd|2026-10-08-claude-code-bash-cd-fails-use-builtin-cd]]"
  - "[[_raw/_archived/2026-10-08-click-clirunner-rich-stderr-console-not-captured|2026-10-08-click-clirunner-rich-stderr-console-not-captured]]"
---

# wyrdcraeft

A local [[concepts/old-english]] morphology project (Python). Session notes from 2026-10-08 record how plans, shells, and CLI tests were checked; they do not restate the generator’s linguistic model.

## Key Concepts

- [[concepts/old-english]] — the language whose inflected forms the generator constructs.
- [[concepts/oe-word-formation]] — affix and compound patterns the toolkit sits beside, not a description of the generator. ^[inferred]
- [[skills/verify-plan-in-throwaway-worktree]] — run a plan’s own code in a detached worktree before executing it on the main tree.
- [[skills/claude-code-builtin-cd]] — `builtin cd` so pytest imports the worktree package, not the editable main checkout.
- [[skills/click-clirunner-rich-stderr]] — CliRunner misses Rich stderr consoles bound at import; monkeypatch the print helper.

## Related

- [[projects/aenglisc-toolkit/aenglisc-toolkit]] — neighbouring OE reading/annotation app; different stack (Qt vs CLI generator). ^[inferred]

## Open Questions

- How the generator’s “entry” count relates to dictionary headwords (DOE vs generated forms) is discussed in an older vault conversation, not in these session notes. ^[ambiguous]

## Sources

- [[_raw/_archived/2026-10-08-verify-plan-code-in-throwaway-git-worktree.md]]
- [[_raw/_archived/2026-10-08-claude-code-bash-cd-fails-use-builtin-cd.md]]
- [[_raw/_archived/2026-10-08-click-clirunner-rich-stderr-console-not-captured.md]]
