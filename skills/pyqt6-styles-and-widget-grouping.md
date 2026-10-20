---
title: "Qt widget styling, grouping, and tabs"
category: "skills"
tags: ["qt", "pyqt", "gui", "python"]
sources: ["book:isbn:9781484279991/chapter/6"]
summary: "Willman separates native styles, rich-text formatting, and widget style sheets, then connects visual grouping to containers and tabs."
provenance: {"extracted": 0.85, "inferred": 0.15, "ambiguous": 0}
base_confidence: 0.5667
lifecycle: "draft"
lifecycle_changed: "2026-10-18"
tier: "supporting"
created: "2026-10-18T19:59:31.689603+00:00"
updated: "2026-10-18T19:59:31.689603+00:00"
snapshots:
  - "[[_raw/_archived/6. Styling Your GUIs|6. Styling Your GUIs]]"
relationships:
  - target: "[[references/beginning-pyqt-willman-2022]]"
    type: derived_from
---

# Qt widget styling, grouping, and tabs

This note distills chapter 6 of [[references/beginning-pyqt-willman-2022|Willman’s Beginning PyQt]].

Chapter 6 distinguishes the application’s underlying style, rich-text presentation, and Qt Style Sheets. It connects appearance to consistency, visual hierarchy, relationships, emphasis, and recurring patterns.

## Styling and structure serve different purposes

| Mechanism | Main role in the chapter |
| --- | --- |
| QStyle and available built-in styles | Base widget appearance |
| Supported HTML in text widgets | Format displayed text |
| Qt Style Sheets | Style widgets and interaction states |
| Object names and selectors | Target particular widgets |
| QGroupBox and containers | Group related controls |
| QTabWidget | Divide content into named pages |

The source contrasts style sheets applied close to an individual widget with styles applied at a broader scope. It also demonstrates interaction-dependent appearances and targeting named widgets. The food-ordering project combines category tabs with shared visual treatment.

[[concepts/ux-cognition]] explains why grouping and contrast affect attention and perception. [[concepts/ux-emotional-interaction]] supplies a wider account of how appearance contributes to experience. [[projects/aenglisc-toolkit/references/qtsass]] is the vault’s separate reference on managing stylesheet source.

## Limits

A property reference from this 2022 chapter is a lookup aid, not evidence that every browser CSS feature works in Qt Style Sheets. Likewise, a consistent stylesheet alone does not establish usability; the proposed interface still needs [[skills/ux-evaluation-planning]]. ^[inferred]

## Sources

- [[_raw/_archived/6. Styling Your GUIs.md]]
