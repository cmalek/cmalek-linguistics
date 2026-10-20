---
title: >-
  qutebrowser
category: references
tags: [qt, python, browser, design]
sources:
  - "url:https://github.com/qutebrowser/qutebrowser"
summary: >-
  qutebrowser: GPL keyboard-driven, vim-like browser on Python and Qt, defaulting to the QtWebEngine backend.
provenance:
  extracted: 0.83
  inferred: 0.17
  ambiguous: 0.0
base_confidence: 0.47
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: peripheral
created: 2026-10-18T18:08:40Z
updated: 2026-10-18T18:08:40Z
snapshots:
  - "[[_raw/_archived/GITHUB qutebrowser 2026-10-17|GITHUB qutebrowser 2026-10-17]]"
---

# qutebrowser

qutebrowser is a keyboard-focused browser with a minimal GUI, built on Python and Qt and licensed GPL (11.7k stars at clip time). It was inspired by dwb and Vimperator/Pentadactyl.

## Key Points

- Requires Python 3.10+, Qt 6.2+ or 5.15+, and PyQt 6.2.2+ (Qt 6) or 5.15+ (Qt 5), plus jinja2 and PyYAML. macOS also needs pyobjc.
- QtWebEngine (Chromium-based) is the default backend. QtWebKit is not recommended because of known security issues.
- Optional: adblock for ABP-syntax blocking, pygments for `:view-source`, asciidoc for `:help` when running from git.
- Bug reports go through a built-in `:report` command, the issue tracker, or a mailing list; security reports have a separate address and GitHub's private reporting.
- The primary maintainer works part-time on it, funded by donations.
- Relevance to [[projects/aenglisc-toolkit/aenglisc-toolkit|aenglisc_toolkit]]: a worked example of a large keyboard-first PyQt application. ^[inferred]

Part of [[projects/aenglisc-toolkit/concepts/qt-app-design-references|Qt app design references]].

## Sources

- [[_raw/_archived/GITHUB qutebrowser 2026-10-17]] — clipping of https://github.com/qutebrowser/qutebrowser (2026-10-17)
