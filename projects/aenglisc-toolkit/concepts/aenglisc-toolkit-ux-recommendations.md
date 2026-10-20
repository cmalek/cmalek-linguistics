---
title: >-
    aenglisc_toolkit: UI flow, missing features and features to drop
category: concepts
tags: [aenglisc-toolkit, ux, interaction-design, desktop-app, accessibility]
relationships:
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-current-capabilities]]"
    type: extends
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-roadmap-trello]]"
    type: related_to
  - target: "[[references/desktop-ux-guidelines-sources]]"
    type: derived_from
  - target: "[[references/interaction-design-5th-edition]]"
    type: derived_from
sources:
  - "[[references/desktop-ux-guidelines-sources]]"
  - "[[references/translation-tools-and-scholarly-editing-standards]]"
  - "[[references/interaction-design-5th-edition]]"
  - "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-roadmap-trello]]"
summary: >-
    Ranked UI and flow changes, feature ideas and features to drop for aenglisc_toolkit, each tied to a guideline or tool and labelled as an inference to prototype and test with the translator.
provenance:
  extracted: 0.30
  inferred: 0.65
  ambiguous: 0.05
base_confidence: 0.45
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T22:30:00Z
updated: 2026-10-18T22:30:00Z
---
	
# aenglisc_toolkit: UI flow, missing features and features to drop

Guidelines are generic and the user is one scholar, so every row below is a hypothesis. [[references/interaction-design-5th-edition]] says to test an alternative before committing ([[skills/ux-prototyping]], [[skills/ux-evaluation-planning]]); a cheap cognitive walk-through of "annotate one sentence" ([[skills/ux-inspections-and-models]]) would settle several rows. The app was not run for this research. ^[inferred]

## UI flow: ranked

| # | Change | Why (source) | Caveat |
|---|---|---|---|
| 1 | Edit the selected token's annotation in the details sidebar, keeping the modal as an "expand" form | Apple, GNOME and NN/g agree that modals suit short, narrow tasks; annotation is frequent and repetitive | The form has many POS-specific fields, so the sidebar may be too small. Prototype first. |
| 2 | Sticky annotation mode: pick a value (for example case: dative), then click tokens to apply it | Zotero's locked mode; Calibre keyboard hints | It must not become auto-annotation: the user chooses each token. |
| 3 | Add a non-colour cue to every highlight mode (underline style, glyph or letter badge), a colour-blind-safe palette, and 4.5:1 text contrast in both themes | Apple HIG and WCAG 1.4.1; Qt: "Do not depend on colors only" | Underline styles are available as `QTextCharFormat` features. |
| 4 | Make bare-letter shortcuts safe: a setting to disable or remap, and scope them to the token view | WCAG 2.1.4; Apple "define custom keyboard shortcuts for only the most frequently used" | WCAG is a web standard, used here as guidance only. The Help Center already lists keys that do not exist (J/K, `Ctrl+Y`). |
| 5 | One `QAction` per command in a full menu bar with disabled-not-hidden items; shortcuts in tooltips | Apple menu bar; Microsoft "rely on an application's menus"; [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-idiom-plan]] item 8 | A command palette is optional on top, per Obsidian. |
| 6 | Named, multi-level undo that scrolls to and selects the change | Apple undo-and-redo; QUndoStack | Fixes the 50-command eviction. |
| 7 | Hideable panes with predictable restore, saved layouts, and a reset-layout command | Apple split views; OmegaT; Obsidian workspaces | Layouts can cover the Backlog "view modes" card. |
| 8 | Trim the toolbars to a few frequent actions; add a hide-chrome reading mode | Apple toolbars | |
| 9 | Keep highlight and view options in the View menu; keep Preferences small; **System / Light / Dark with System as default** (decided 2026-10-18) | Apple settings and dark mode | Both themes stay because users depend on them; code changes are on [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-os-integration]]. |
| 10 | Empty-state text on a fresh project; one status line for progress and errors | GNOME placeholders; Apple feedback | Autosave failures need a visible message (verified silent today). |

## Missing features worth considering

The tool evidence is in [[references/translation-tools-and-scholarly-editing-standards]]; all are manual-safe.

- **Glossary pane for the current sentence**, lit from the user's own annotations (OmegaT's Glossaries pane). Data exists already.
- **Consistency check**: the same root glossed two ways (Weblate "Inconsistent"), with an ignore flag per root. Useful because remembered annotations match spelling only.
- **Sentence status** (untranslated, draft, needs work, done, reviewed), filterable, and a report of un-annotated or low-confidence tokens. This extends the TODO marker and the Backlog "spot un-annotated words" card. A "N of M annotated" counter is my idea; no source was found for it. ^[inferred]
- **Annotation list that jumps to the sentence** (Calibre highlights panel, Zotero annotations tab).
- **Reopen at the last position** and per-project view state.
- Output-side items are on [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-academic-output-plan]].

## Features to drop or avoid

1. **Remembered-annotation propagation as silent pre-fill: revised.** After the owner described their use (store only what is known on sight, leave the ambiguous cells open), this is not a pre-fill risk in the bias sense; it is the translator's own partial judgment. Two smaller fixes remain: a *derived* "needs context" state so a partial token does not look finished, and an option to leave meaning and sense out of remembered templates. See [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-remembered-annotations-and-bias]]. ^[inferred]
2. **Gamification** (streaks, scores, badges): no support for a single-user scholarly tool.
3. **Startup tray balloon**, and any push-style "what's new" popups. NN/g and Apple prefer optional, contextual help.
4. **A second way to do everything** (toolbar button, bare key, menu, palette) beyond what the guidelines call for; Microsoft's "make the hard decision" applies.
5. **Sentence diagramming and a user-built dictionary** until they earn a place against the daily read-annotate-translate loop. Both are large; neither has outside evidence here. ^[inferred]
6. **Do not add**: translation memory, MT or LLM suggestion panes, recommenders, team review workflows, TBX or XLIFF as core storage (see [[concepts/manual-translation-workbench-features]]).

## Open Questions

- Does an editable sidebar keep up with the full POS form, or does it need two tiers (fast fields, expanded fields)?
- Which highlight mode does the user rely on most? Fewer modes means fewer colours to make accessible.
- Are the on-deck bugs (line-initial words, capitalised words) a trust problem that should come before any of this? Probably, since they silently skip data. ^[inferred]

## Related

- [[projects/aenglisc-toolkit/aenglisc-toolkit]]
- [[concepts/ux-cognition]]
- [[concepts/ux-interface-selection]]
- [[synthesis/Research: Qt and Translation Workbench Best Practice]]

## Sources

- [[references/desktop-ux-guidelines-sources]]
- [[references/translation-tools-and-scholarly-editing-standards]]
- [[references/ai-disclosure-and-suggestion-bias-sources]]
