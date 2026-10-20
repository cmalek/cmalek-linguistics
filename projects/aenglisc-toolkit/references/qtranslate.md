---
title: >-
  QTranslate (plugin-based translation suite)
category: references
tags: [translation, desktop-app, plugins, design]
sources:
  - "url:https://github.com/ahatem/QTranslate"
summary: >-
  QTranslate: Kotlin desktop translation suite where translators, OCR, TTS, spell check and dictionaries are runtime-swappable plugins.
provenance:
  extracted: 0.88
  inferred: 0.12
  ambiguous: 0.0
base_confidence: 0.47
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: peripheral
created: 2026-10-18T18:08:40Z
updated: 2026-10-18T18:08:40Z
snapshots:
  - "[[_raw/_archived/GITHUB QTranslate 2026-10-18|GITHUB QTranslate 2026-10-18]]"
---

# QTranslate (plugin-based translation suite)

QTranslate is a free, open source desktop translation suite (Windows, macOS, Linux; 250 stars at clip time; 99.3% Kotlin). Despite the name it is not a Qt application. It is a from-scratch rebuild of an abandoned earlier tool of the same name.

## Key Points

- Core flow: select text in any application, press `Ctrl+Q`, read the result in a popup without leaving the work.
- Design lesson stated by the author: a translation app should not die because one service changes its API, so engines, OCR, TTS, spell checkers, dictionaries and AI services are plugins replaceable independently. JAR plugins install without a restart.
- Parallel comparison shows several providers' translations side by side; backward translation shows the round-trip to spot awkward phrasing.
- Reference panels: Wiktionary for words and Wikimedia Commons for images, with licence and source shown.
- Document translation covers DOCX, PDF, TXT, SRT and VTT. DOCX structure and subtitle timing are preserved; PDF layout is rebuilt best-effort.
- Privacy: AI features can point to a local Ollama or LM Studio endpoint, or a self-hosted LibreTranslate server. Third-party plugin JARs run with local access, so only trusted publishers should be installed.
- Packaging: the Windows zip bundles Java; macOS and Linux need Java 17+.
- Relevance to [[projects/aenglisc-toolkit/aenglisc-toolkit|aenglisc_toolkit]]: the select-then-lookup flow and the plugin boundary both fit a reading tool that consults dictionaries such as [[entities/bosworth-toller]]. ^[inferred]

Part of [[projects/aenglisc-toolkit/concepts/qt-app-design-references|Qt app design references]].

## Sources

- [[_raw/_archived/GITHUB QTranslate 2026-10-18]] — clipping of https://github.com/ahatem/QTranslate (2026-10-18)
