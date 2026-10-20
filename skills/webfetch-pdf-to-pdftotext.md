---
title: >-
  WebFetch on a PDF URL returns binary; use pdftotext on the saved file
category: skills
tags: [research-tooling, pdf, wiki-research]
sources:
  - "agent:cmalek-linguistics-session-2026-10-17"
relationships:
  - target: "[[skills/linguistic-pdf-to-markdown]]"
    type: related_to
  - target: "[[synthesis/Research: Scholarly PDF to Markdown]]"
    type: related_to
  - target: "[[skills/obsidian-wiki-snapshots-set-vault-relative]]"
    type: related_to
summary: >-
  WebFetch cannot summarize PDFs, but it saves the file under tool-results/. Run pdftotext on that path with absolute paths, then read the text.
provenance:
  extracted: 0.9
  inferred: 0.1
  ambiguous: 0.0
base_confidence: 0.6
lifecycle: draft
lifecycle_changed: "2026-10-17"
tier: supporting
created: 2026-10-17T18:40:00Z
updated: 2026-10-17T18:40:00Z
snapshots:
  - "[[_raw/_archived/2026-10-17-webfetch-pdf-returns-binary|2026-10-17-webfetch-pdf-returns-binary]]"
---

# WebFetch on a PDF URL returns binary; use pdftotext on the saved file

WebFetch on a PDF URL (a journal PDF, a repository bitstream) answers that the text is unreadable, because it sees compressed streams. The result also says the binary was saved as a `.pdf` under the session's `tool-results/` directory.

## Pattern

Run `pdftotext -layout <saved.pdf> <scratchpad>/out.txt` with absolute paths, then Read or grep the text. In the 2026-10-17 session this recovered a 22-page journal article and a 300-page dissertation in full.

## Related quirks

- `cd dir && cmd` failed in the Bash tool: use `/usr/bin/cd`. Use absolute paths. See [[skills/claude-code-builtin-cd]].
- `~/.config/obsidian-wiki` did not exist, so `/wiki-switch <name>` had no profile to switch to; the vault was found from the working directory.

## Sources

- [[_raw/_archived/2026-10-17-webfetch-pdf-returns-binary|2026-10-17-webfetch-pdf-returns-binary]]
