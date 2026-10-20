---
title: "Qt signals, slots, and event handlers"
category: "skills"
tags: ["qt", "pyqt", "gui", "python"]
sources: ["book:isbn:9781484279991/chapter/7"]
summary: "Signals connect object behavior; event handlers specialize responses to delivered keyboard, mouse, and other events."
provenance: {"extracted": 0.85, "inferred": 0.15, "ambiguous": 0}
base_confidence: 0.5667
lifecycle: "draft"
lifecycle_changed: "2026-10-18"
tier: "supporting"
created: "2026-10-18T19:59:31.689603+00:00"
updated: "2026-10-18T19:59:31.689603+00:00"
snapshots:
  - "[[_raw/_archived/7. Handling Events in PyQt|7. Handling Events in PyQt]]"
relationships:
  - target: "[[references/beginning-pyqt-willman-2022]]"
    type: derived_from
---

# Qt signals, slots, and event handlers

This note distills chapter 7 of [[references/beginning-pyqt-willman-2022|Willman’s Beginning PyQt]].

Chapter 7 presents two complementary tools for GUI behavior. Signals notify connected receivers and may carry data. Event objects describe interactions delivered through the event system, and handlers implement the receiving widget’s response.

## Choose the boundary

| Need | Mechanism demonstrated |
| --- | --- |
| React to a widget’s existing notification | Connect a signal to a slot |
| Pass application-specific data between objects | Define a custom pyqtSignal |
| Change keyboard behavior | Reimplement keyPressEvent or keyReleaseEvent |
| Change mouse behavior | Reimplement the relevant mouse handler |
| Track movement without a pressed button | Enable mouse tracking for the widget |

The chapter sends key events to the widget with keyboard focus and distinguishes press, release, movement, double-click, and pointer entry or exit. Its examples change label styling through custom signals rather than making every communicating object know the other’s implementation.

When extending an existing event handler, the source describes passing through to the base behavior for functionality the override does not handle. Preserve that decision explicitly when specializing a widget.

[[skills/pyqt6-custom-widgets]] uses both composition and specialized behavior. [[projects/aenglisc-toolkit/skills/qt-extraselection-highlight-layers]] is an existing application-specific example of maintaining editor behavior and presentation, while [[concepts/ux-conceptual-models]] connects events to the actions users intend.

These notes preserve the conceptual distinction. They do not assert that the chapter’s brief prose exhaustively classifies every event or signal source.

## Sources

- [[_raw/_archived/7. Handling Events in PyQt.md]]
