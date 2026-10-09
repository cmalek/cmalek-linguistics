---
title: "Qt ExtraSelection highlight layers: gotchas found reviewing a compositor design"
category: skills
tags:
  - topic/pyside6
  - topic/qt
  - design/adr-review
summary: "Competing setExtraSelections writers wipe each other; a layered compositor must anchor entries by token, not offset, resolve colours at compose time, and not use isinstance on subclassed editors."
tier: supporting
related: []
extends: null
contradicts: null
superseded_by: null
capture_source: claude-session
project: "aenglisc_toolkit"
base_confidence: 0.75
lifecycle: draft
lifecycle_changed: 2026-10-02
provenance:
  extracted: 0.7
  inferred: 0.3
sources:
  - "aenglisc_toolkit session (2026-10-02)"
---

Findings from designing (ADR 0004) and adversarially reviewing a fix for several writers fighting over one `QTextEdit.setExtraSelections` list. Verified by reading code; not yet implemented.

## setExtraSelections replaces the whole list

**Behavior:** Each writer must read `extraSelections()`, filter by a property tag, merge, and write back. One writer calling `setExtraSelections([])` (here, mode `unhighlight`, reached via entering edit mode) silently wipes every other writer's highlights, including search.

**Pattern:** One owner composes named layers (mode, span, search) in a fixed paint order (later list entries paint on top) and calls `setExtraSelections` once. Highlighters only set or clear their own layer.

## Stored cursors and document offsets die on re-render

**Behavior:** An ExtraSelection holds a `QTextCursor` bound to the document. Rebuilding the document (here, inserting note superscripts) invalidates stored cursors, and offsets shift because the inserted characters sit between tokens.

**Pattern:** Store layer entries as token anchors (first/last token id plus a style) and resolve to offsets at compose time through the editor's token-to-position map, filled during render. Compose at the end of the render, and write nothing while the editor is editable.

## Review catches on the design

- **isinstance on a subclassed editor:** the full-translation-window editor subclasses the sentence editor but keeps its own position map. `isinstance` dispatch would route it into the layer path and resolve nothing; use an explicit capability attribute.
- **Baked colours:** the app recomputes palette-derived colours on live theme switch. Layer entries should carry a semantic style key resolved against the palette at compose time, including the dark-theme foreground, not a concrete colour.
- **Per-compose scans:** a text-pattern search layer that runs `document.find` on every compose rescans the document on every token click; cache resolved ranges until the next render.
- **"Preserves today's behaviour" claims:** check them. Here the old mode writer kept only search-tagged selections, so changing mode dropped the selected-span highlight; independent layers change that.
- **Re-running search after an edit:** needs a named per-card entry point and an owner of the query state, not "the same path a fresh search uses".

**Confirmed by:** Reading the code paths; no tests run yet.
