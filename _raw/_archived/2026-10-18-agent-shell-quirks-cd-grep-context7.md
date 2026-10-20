---
title: "Agent shell quirks: cd function, grep alternation, missing Context7"
category: skills
tags:
  - topic/claude-code
  - shell
  - workflow
summary: "In this setup bare cd is a broken shell function, /usr/bin/cd does not persist, grep \\| fails under ugrep, and Context7 tools may be absent."
tier: peripheral
related: []
extends: null
contradicts: null
superseded_by: null
capture_source: claude-session
project: "aenglisc_toolkit"
base_confidence: 0.75
lifecycle: draft
lifecycle_changed: 2026-10-18
provenance:
  extracted: 0.85
  inferred: 0.15
sources:
  - "aenglisc_toolkit session (2026-10-18)"
---

## Bare `cd` breaks the agent shell

**Behavior:** Bash calls fail with `chdir: command not found` from the shell snapshot, and `cd dir && cmd` does not work. The repo's `AGENTS.md` says: always use `/usr/bin/cd`; bare `cd` is a bash function that breaks agent shells. The user also told the agent to use `/usr/bin/cd`.

**Explanation:** `/usr/bin/cd` runs as its own process, so the directory change is lost when it exits. `/usr/bin/cd dir && cmd` still runs `cmd` in the old directory, and the reads failed with "No such file".

**Workaround / Pattern:** Use absolute paths in every command (`R=/path; cat $R/file`), or `git -C <repo>`. Use `/usr/bin/cd` only where its exit status is wanted.

**Confirmed by:** Reads failed with `/usr/bin/cd` chained, and worked with absolute paths.

## `grep` with `\|` fails here

**Behavior:** `grep -rlE "a\|b"` style patterns (BRE alternation) and unescaped `(` raised ugrep "mismatched ( )" errors, and counts came back as false zeros.

**Workaround / Pattern:** Use `grep -E "a|b"` with escaped literal parens (`QAction\(`). Treat a zero count from a failed pattern with suspicion and rerun.

**Confirmed by:** Rerun with `-E` gave non-zero counts for QAction, QTableWidget, QSplitter and others.

## Context7 tools may not be exposed

**Behavior:** A user instruction asked for Context7, but `ToolSearch` for "context7 resolve-library-id query-docs" found no tool.

**Workaround / Pattern:** Say so in the output. Fetch official docs with `WebFetch` (for example `doc.qt.io/qt-6/...`) and mark which claims rest on those pages and which on general knowledge.

**Notes:** `WebFetch` truncates long pages (the Model/View page was cut at 100,000 of 139,925 characters); use `offset` to read on.
