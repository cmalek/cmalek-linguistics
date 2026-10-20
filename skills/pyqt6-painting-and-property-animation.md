---
title: "Qt painting, graphics scenes, and property animation"
category: "skills"
tags: ["qt", "pyqt", "gui", "python"]
sources: ["book:isbn:9781484279991/chapter/11"]
summary: "QPainter draws on paint devices; Graphics View manages scenes and items; property animation changes exposed object properties over time."
provenance: {"extracted": 0.8, "inferred": 0.15, "ambiguous": 0.05}
base_confidence: 0.5667
lifecycle: "draft"
lifecycle_changed: "2026-10-18"
tier: "supporting"
created: "2026-10-18T19:59:31.689603+00:00"
updated: "2026-10-18T19:59:31.689603+00:00"
snapshots:
  - "[[_raw/_archived/11. Graphics and Animation in PyQt|11. Graphics and Animation in PyQt]]"
relationships:
  - target: "[[references/beginning-pyqt-willman-2022]]"
    type: derived_from
---

# Qt painting, graphics scenes, and property animation

This note distills chapter 11 of [[references/beginning-pyqt-willman-2022|Willman’s Beginning PyQt]].

Chapter 11 develops painting and animation as related but distinct mechanisms. QPainter performs drawing operations, a QPaintDevice supplies a drawing surface, and QPaintEngine supports the underlying drawing implementation.

## Keep the mechanisms distinct

| Mechanism | Elements in the chapter |
| --- | --- |
| Painting | QPainter with colors, pens, brushes, shapes, text, and images |
| Widget repainting | paintEvent and a maintained canvas image |
| Graphics View | A scene, a view, and graphical items |
| Property animation | QPropertyAnimation targeting exposed properties |
| Custom property | A property defined with pyqtProperty where needed |

The painter project combines a canvas with mouse input, drawing tools, color selection, saving, and antialiasing controls. Graphics View instead manages items in a scene that a view presents. The animation examples change properties of objects or widgets over time.

The source sometimes spells the animation class QAnimationProperty in prose, while its heading and examples use QPropertyAnimation. Preserve the example’s spelling when looking up the mechanism. ^[ambiguous]

[[skills/pyqt6-custom-widgets]] connects painting with specialized controls. [[concepts/ux-emotional-interaction]] supplies a context for expressive motion, and [[projects/aenglisc-toolkit/skills/qt-extraselection-highlight-layers]] documents a different, text-editor-specific presentation mechanism.

## Application question

Is the problem a custom drawing surface, a set of independently managed scene items, or a change to an existing property? Choosing that boundary first avoids treating all visual behavior as one drawing problem. ^[inferred]

## Sources

- [[_raw/_archived/11. Graphics and Animation in PyQt.md]]
