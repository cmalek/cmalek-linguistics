---
title: >-
  Agent search quirks: grep alternation and missing Context7
category: skills
tags: [shell, tooling, research-tooling, workflow]
relationships:
  - target: "[[skills/claude-code-builtin-cd]]"
    type: related_to
  - target: "[[skills/webfetch-pdf-to-pdftotext]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-practice-gap-analysis]]"
    type: related_to
sources:
  - "agent:aenglisc-toolkit-session-2026-10-18"
summary: >-
  In this setup grep rejects BRE-style \| alternation and returns false zero counts; use grep -E. Context7 tools may be absent, so fetch official docs with WebFetch and say which claims they support.
provenance:
  extracted: 0.85
  inferred: 0.15
  ambiguous: 0.0
base_confidence: 0.5
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: peripheral
created: 2026-10-18T21:00:00Z
updated: 2026-10-18T21:00:00Z
snapshots:
  - "[[_raw/_archived/2026-10-18-agent-shell-quirks-cd-grep-context7|2026-10-18-agent-shell-quirks-cd-grep-context7]]"
---

# Agent search quirks: grep alternation and missing Context7

Two small tooling traps from the [[projects/aenglisc-toolkit/aenglisc-toolkit|aenglisc_toolkit]] research session. The shell `cd` trap has its own page: [[skills/claude-code-builtin-cd]].

## `grep` alternation gives false zeros

- Patterns such as `"a\|b"` and an unescaped `(` (for example `QAction(`) made `grep` fail with a "mismatched ( )" error, so a count loop printed `0 files / 0 hits` for features that exist.
- Rerunning with `grep -E "a|b"` and escaped literal parentheses (`QAction\(`) gave real counts (24 `QAction(` hits, 44 item-widget hits, and others).
- Treat any zero from a pattern loop as unverified until the error output is clear. The wrong zeros would otherwise have gone into a gap analysis as "not used". ^[inferred]

## Context7 may not be exposed

- A user instruction asked for Context7, but `ToolSearch` for `context7 resolve-library-id query-docs` found no matching tool.
- What worked: state the gap in the output, then use `WebFetch` on the official docs (here `doc.qt.io/qt-6/...`) and record which claims rest on a fetched page and which on general knowledge.
- `WebFetch` truncates long pages. The Qt Model/View page was cut at 100,000 of 139,925 characters; the tool's `offset` argument reads the rest.

## Sources

- [[_raw/_archived/2026-10-18-agent-shell-quirks-cd-grep-context7.md]]
