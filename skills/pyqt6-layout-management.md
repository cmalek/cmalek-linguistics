---
title: "Choosing and combining Qt widget layouts"
category: "skills"
tags: ["qt", "pyqt", "gui", "python"]
sources: ["book:isbn:9781484279991/chapter/4"]
summary: "Box, grid, form, and stacked layouts organize widgets while size hints, policies, stretch, and margins govern space."
provenance: {"extracted": 0.85, "inferred": 0.15, "ambiguous": 0}
base_confidence: 0.5667
lifecycle: "draft"
lifecycle_changed: "2026-10-18"
tier: "supporting"
created: "2026-10-18T19:59:31.689603+00:00"
updated: "2026-10-18T19:59:31.689603+00:00"
snapshots:
  - "[[_raw/_archived/4. Learning About Layout Management|4. Learning About Layout Management]]"
relationships:
  - target: "[[references/beginning-pyqt-willman-2022]]"
    type: derived_from
---

# Choosing and combining Qt widget layouts

This note distills chapter 4 of [[references/beginning-pyqt-willman-2022|Willman’s Beginning PyQt]].

Chapter 4 treats layout as management of widget position and size as the available space and child widgets change. Absolute positioning fixes coordinates; layout managers express relationships among widgets and let their placement respond to changes.

## Layout choices

| Arrangement | Layout |
| --- | --- |
| A horizontal row | QHBoxLayout |
| A vertical column | QVBoxLayout |
| Rows and columns, including spans | QGridLayout |
| Label–field pairs | QFormLayout |
| Pages sharing the same space | QStackedLayout |

Nested layouts combine these arrangements: a horizontal group can sit inside a vertical parent, and grids can span widgets across cells. A stacked layout also needs a way to choose the current page; the chapter uses a combo box.

## How space is allocated

The chapter identifies size hints, size policies, stretch factors, and minimum or maximum sizes as inputs to layout allocation. Spacing, stretchable gaps, and content margins solve different parts of the space problem. A form expresses a label–field relationship without repeatedly calculating coordinates.

[[concepts/ux-cognition]] explains why grouping and spacing matter to perception. [[concepts/ux-interface-selection]] supplies the activity constraints that a layout needs to serve. [[skills/pyqt6-designer-workflow]] shows how to assign the same kinds of layouts visually.

## Practical implication

Choose a layout for a local relationship, then nest it with other relationships. Treating every widget as a manually positioned rectangle discards the structure that the layout manager could otherwise maintain. ^[inferred]

## Sources

- [[_raw/_archived/4. Learning About Layout Management.md]]
