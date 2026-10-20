---
title: "WebFetch on PDF URLs returns binary; extract the saved file with pdftotext"
category: skills
tags:
  - topic/wiki-research
  - research-tooling
  - pdf
summary: "WebFetch cannot summarize PDFs (compressed streams), but it saves the file under tool-results/. Run pdftotext on that path and Read the text."
tier: supporting
related: []
extends: null
contradicts: null
superseded_by: null
capture_source: claude-session
project: "cmalek-linguistics"
base_confidence: 0.85
lifecycle: draft
lifecycle_changed: 2026-10-17
provenance:
  extracted: 0.9
  inferred: 0.1
sources:
  - "cmalek-linguistics session (2026-10-17)"
---

## WebFetch on a PDF URL gives no usable text

**Behavior:** WebFetch on a PDF URL (a journal PDF, a university repository bitstream) answers "the text isn't readable" because it sees FlateDecode streams. The result does say "Binary content ... also saved to <path>.pdf" under the session's `tool-results/` directory.

**Workaround / Pattern:** Run `pdftotext -layout <saved.pdf> <scratchpad>/out.txt` using absolute paths, then Read or grep the text. In this session it recovered a 22-page journal article and a 300-page dissertation in full.

**Confirmed by:** both PDFs converted and read.

**Notes:**
- `cd` in the Bash tool failed here ("chdir: command not found"), so use absolute paths instead of `cd dir && ...`.
- Paths in `~/.config/obsidian-wiki` did not exist; the vault was found from the working directory. A missing named profile means `/wiki-switch` cannot switch.
- Related: [[synthesis/Research: Scholarly PDF to Markdown]].
