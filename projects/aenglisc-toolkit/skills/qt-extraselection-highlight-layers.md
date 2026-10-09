---
title: >-
    Qt ExtraSelection Highlight Layers
category: skills
tags: [qt, python, workflow]
relationships:
  - target: "[[projects/aenglisc-toolkit/aenglisc-toolkit]]"
    type: related_to
sources:
  - "agent:aenglisc-toolkit-session-2026-10-02"
summary: >-
    Competing setExtraSelections writers wipe each other; a compositor should own named layers, anchor by token, and resolve colours at compose time. Reviewed, not implemented.
provenance:
  extracted: 0.70
  inferred: 0.30
  ambiguous: 0.00
base_confidence: 0.42
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T15:54:00Z
updated: 2026-10-09T15:54:00Z
snapshots:
  - "[[_raw/_archived/2026-10-02-qt-extraselection-highlight-layers|2026-10-02-qt-extraselection-highlight-layers]]"
---

# Qt ExtraSelection Highlight Layers

Design notes (ADR 0004) from reviewing several writers fighting over one `QTextEdit.setExtraSelections` list in [[projects/aenglisc-toolkit/aenglisc-toolkit]]. Verified by reading code; not implemented; no tests run.

## Key Ideas

**`setExtraSelections` replaces the whole list.** Each writer must read `extraSelections()`, filter by a property tag, merge, and write back. One writer calling `setExtraSelections([])` (mode `unhighlight`, via entering edit mode) silently wipes every other writer’s highlights, including search. Pattern: one owner composes named layers (mode, span, search) in a fixed paint order (later entries on top) and calls `setExtraSelections` once. Highlighters only set or clear their own layer.

**Stored cursors and document offsets die on re-render.** An ExtraSelection holds a `QTextCursor` bound to the document. Rebuilding (inserting note superscripts) invalidates stored cursors; offsets shift because inserted characters sit between tokens. Pattern: store layer entries as token anchors (first/last token id plus a style) and resolve offsets at compose time through the editor’s token-to-position map, filled during render. Compose at the end of render; write nothing while the editor is editable.

**Review catches**

- The full-translation-window editor subclasses the sentence editor but keeps its own position map. `isinstance` dispatch would take the layer path and resolve nothing; use an explicit capability attribute.
- The app recomputes palette-derived colours on live theme switch. Layer entries should carry a semantic style key resolved against the palette at compose time, including dark-theme foreground, not a baked colour.
- A text-pattern search layer that runs `document.find` on every compose rescans on every token click; cache resolved ranges until the next render.
- The old mode writer kept only search-tagged selections, so changing mode dropped the selected-span highlight. Independent layers change that; do not claim “preserves today’s behaviour” without checking.
- Re-running search after an edit needs a named per-card entry point and an owner of the query state.

## Open Questions

- Whether the compositor ships as designed; this page is a review of a proposal, not a record of merged code. ^[inferred]

## Sources

- [[_raw/_archived/2026-10-02-qt-extraselection-highlight-layers.md]]
