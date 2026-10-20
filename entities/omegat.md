---
title: >-
    OmegaT
category: entities
tags: [translation, cat-tools, tooling, desktop-app]
relationships:
  - target: "[[references/translation-tools-and-scholarly-editing-standards]]"
    type: derived_from
  - target: "[[concepts/manual-translation-workbench-features]]"
    type: related_to
sources:
  - "https://omegat.sourceforge.io/manual-latest/en/chapter.project.folder.html"
  - "https://omegat.sourceforge.io/manual-latest/en/chapter.panes.html"
summary: >-
    Free desktop CAT tool with dockable panes, a segment-matched glossary pane and a plain project folder; it also auto-inserts translation-memory matches, the part a manual tool must skip.
provenance:
  extracted: 0.70
  inferred: 0.25
  ambiguous: 0.05
base_confidence: 0.55
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: peripheral
created: 2026-10-18T22:40:00Z
updated: 2026-10-18T22:40:00Z
---

# OmegaT

A free computer-assisted translation (CAT) desktop application. The manual's own aim is "to help you create a good translation the fastest possible by giving you access to your translation ressources". Read in part (panes and project-folder chapters) on 2026-10-18.

## Worth borrowing

- Dockable panes (editor, glossary, matches) that drag, tab, minimise and undock, with a "Restore OmegaT Window" command; a closed pane's tab flashes when it has content for the current segment.
- A glossary pane that shows terms matching the current segment, with a shortcut to add an entry from the editor.
- A project as a plain folder (`source`, `target`, `tm`, `glossary`) with a backup of the project file.

## Not for a manual tool

Translation-memory folders `tm/auto` and `tm/enforce` insert matched translations into segments automatically, and fuzzy-match and machine-translation panes exist. See [[concepts/manual-translation-workbench-features]].

## Related

- [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ux-recommendations]]
- [[projects/aenglisc-toolkit/references/qtranslate]]

## Sources

- [[references/translation-tools-and-scholarly-editing-standards]]
