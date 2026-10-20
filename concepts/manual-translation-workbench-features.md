---
title: >-
    Manual translation workbench: which features fit and which do not
category: concepts
tags: [translation, tooling, ux, cat-tools, ethics]
relationships:
  - target: "[[references/translation-tools-and-scholarly-editing-standards]]"
    type: derived_from
  - target: "[[references/ai-disclosure-and-suggestion-bias-sources]]"
    type: derived_from
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ux-recommendations]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/references/qtranslate]]"
    type: related_to
sources:
  - "[[references/translation-tools-and-scholarly-editing-standards]]"
  - "[[references/ai-disclosure-and-suggestion-bias-sources]]"
summary: >-
    A triage of translation-tool features for a scholar who translates by hand: those that surface the translator's own work are safe, those that fill in target text are not.
provenance:
  extracted: 0.30
  inferred: 0.65
  ambiguous: 0.05
base_confidence: 0.50
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T22:30:00Z
updated: 2026-10-18T22:30:00Z
---

# Manual translation workbench: which features fit and which do not

A working test: **does the feature show the translator's own earlier work or reference material, or does it write a candidate into the target?** The first kind is safe; the second is the automation that a manual scholarly tool excludes. The test is the vault's synthesis of the tool sources, not a published rule. ^[inferred]

| Feature | Source | Safe for manual work | Why |
|---|---|---|---|
| Glossary pane lit for the current segment, from the user's own entries | OmegaT, Weblate | yes | Surfaces own work |
| Consistency check (one term, two renderings) | Weblate "Inconsistent" | yes | Flags, never rewrites |
| Per-segment status and an "unfinished" report | Weblate states | yes | Bookkeeping |
| Concordance search over own text | OmegaT | yes | Search |
| Dockable panes with a reset command | OmegaT | yes | Layout |
| Autosave and a plain, backed-up project folder | OmegaT | yes | Data safety |
| Source record per gloss | Bosworth-Toller citation, Recogito | yes | Provenance |
| Translation memory auto-insert, fuzzy matches | OmegaT `tm/auto`, `tm/enforce` | **no** | Writes candidates into the target |
| MT or LLM suggestion panes | OmegaT, MateCat | **no** | Translation by machine |
| Recommenders, active learning | INCEpTION | **no** | Machine-made suggestions, even if "accepted" |
| Auto-annotation of POS, case or lemma by a tagger | taggers generally | **no** | Same |
| Team review, approval roles, suggestion voting | Weblate | not needed | Overhead for one translator |
| Volume analysis, word-count pricing | CAT suites | not needed | Commercial |
| TBX, XLIFF, TMX as the data model | standards bodies | not needed | Localisation formats |
| AI context pane, pulled and labelled | COPE, MLA, Chicago rules | risky | See [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ai-context-policy]] |

## Grey area: reuse of the translator's own history

A "remembered annotation" fills fields from the user's earlier decisions. It is not machine translation, and when the translator stores only what is certain on sight and leaves ambiguous cells empty, it behaves like a personal glossary entry. It shares one failure mode with fuzzy TM: a reused value can make a token look finished. The mitigation is a derived "needs context" state, not removal, and keeping rendered meanings out of reusable templates. See [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-remembered-annotations-and-bias]].

## Related

- [[references/translation-tools-and-scholarly-editing-standards]]
- [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-intent]]
- [[skills/translating-ancient-texts]]

## Sources

- [[references/translation-tools-and-scholarly-editing-standards]]
- [[references/ai-disclosure-and-suggestion-bias-sources]]
