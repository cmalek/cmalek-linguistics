---
title: >-
  MuseScore Studio
category: references
tags: [qt, qml, notation, design]
sources:
  - "url:https://github.com/musescore/MuseScore"
summary: >-
  MuseScore Studio: GPL-3.0 C++/QML music notation editor with WYSIWYG entry, MusicXML/MIDI/MEI exchange and a shared muse_framework submodule.
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
  - "[[_raw/_archived/GITHUB MuseScore 2026-10-17|GITHUB MuseScore 2026-10-17]]"
---

# MuseScore Studio

MuseScore Studio is open source music notation software (15.3k stars at clip time; C++ 71.2%, QML 6.5%), licensed GPL-3.0.

## Key Points

- WYSIWYG design: notes are entered on a "virtual notepaper", with TrueType fonts so printing and display scale cleanly.
- Exchange formats: MusicXML, MIDI (SMF) and MEI import and export; MuseData import; MIDI keyboard input.
- Has an integrated sequencer and software synthesizer, and prints or exports PDF.
- Shared UI code lives in the `muse_framework` git submodule, checked out into `muse/`, so clones need `--recurse-submodules`.
- Release build command is `cmake -P build.cmake -DCMAKE_BUILD_TYPE=Release`.
- Relevance to [[projects/aenglisc-toolkit/aenglisc-toolkit|aenglisc_toolkit]]: a model for a specialist text-like document editor whose rendering is the product. ^[inferred]

Part of [[projects/aenglisc-toolkit/concepts/qt-app-design-references|Qt app design references]].

## Sources

- [[_raw/_archived/GITHUB MuseScore 2026-10-17]] — clipping of https://github.com/musescore/MuseScore (2026-10-17)
