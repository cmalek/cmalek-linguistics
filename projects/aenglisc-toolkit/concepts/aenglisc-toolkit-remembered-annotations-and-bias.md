---
title: >-
    aenglisc_toolkit: remembered annotations and suggestion bias
category: concepts
tags: [aenglisc-toolkit, annotation, ux, automation-bias, translation]
relationships:
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-intent]]"
    type: extends
  - target: "[[references/ai-disclosure-and-suggestion-bias-sources]]"
    type: derived_from
  - target: "[[concepts/manual-translation-workbench-features]]"
    type: related_to
sources:
  - "[[references/ai-disclosure-and-suggestion-bias-sources]]"
  - "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-roadmap-trello]]"
  - "user statement 2026-10-18 on how remembered annotations are used"
  - "repo:/Users/cmalek/src/personal/aenglisc_toolkit @ 981e093 (models/remembered_annotation.py, commands/annotation.py)"
summary: >-
    The owner's practice of storing only what is known on sight makes remembered annotations the translator's own partial judgment, not a suggestion; the remaining risks are look-alike completeness and a stored meaning field.
provenance:
  extracted: 0.30
  inferred: 0.60
  ambiguous: 0.10
base_confidence: 0.50
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T23:30:00Z
updated: 2026-10-18T23:30:00Z
---

# aenglisc_toolkit: remembered annotations and suggestion bias

## How the owner uses them

Store the **least** annotation that is true on sight, whatever the context. Example from the owner: *menn* is plural nominative and accusative and singular dative of *mann*, a masculine i-mutation noun, so the remembered entry records the noun, the gender and the class, and leaves the cell open. The case-and-number decision stays with the translator in each sentence.

## What the code allows (read 2026-10-18)

- A remembered annotation is a token-only template keyed on exact `Token.surface`; every field is nullable, so a partial template is the normal case. `case` and `number` are single-valued (one of `n a g d i`, one of `s p`), so a set of possible cells cannot be stored; leaving them empty is the only honest option.
- It also has `modern_english_meaning` and `root`. The batch apply is an undoable command (`ApplyRememberedAnnotationsCommand`); the command code mentions neither confidence nor the TODO marker, so applied fields carry no flag showing where they came from.

## Where it sits against the bias evidence

The suggestion-bias studies concern **candidates written by an outside system into the target** ([[references/ai-disclosure-and-suggestion-bias-sources]]). A remembered annotation differs on three counts: the translator authored it; it concerns grammatical analysis, not the Modern English rendering; and it is deliberately partial. By the vault's own test (does the feature show the translator's earlier work, or write a candidate?) it is safe ([[concepts/manual-translation-workbench-features]]). It is closest to a translator-maintained glossary entry, which OmegaT and Weblate both treat as ordinary. ^[inferred]

## Residual risks

1. **Partial looks complete.** A token with three fields from a template reads like a token the translator analysed in context. Later the owner cannot tell "known on sight" from "decided here", and any count, glossary line or consistency check treats them alike. A *derived* "needs context" state fixes this without storing anything: for each part of speech, list the fields the owner usually fills, and flag a token whose fields are still empty. The same state gives an honest "N of M tokens fully annotated" counter and feeds the Backlog card on un-annotated words. ^[inferred]
2. **Same surface, different word.** Matching is on spelling only, so *hild* (m. "battle", f. "safety") and *þā* get the same template. The owner's minimal style already limits the harm; the Backlog documentation card should say so.
3. **A stored meaning is a pre-filled gloss.** If a template carries `modern_english_meaning`, applying it writes a rendering the translator has not yet chosen for this sentence, which is the anchoring case. The owner's description does not include meanings. A setting to leave meaning and sense out of remembered templates (or out of batch apply) would keep the feature on the safe side. ^[inferred]
4. **Matching bugs hide data.** The On Deck cards (capitalised and line-initial words skipped, *Hē*, *Hī*) all trace to the exact-surface lookup in `matching_tokens`. A word skipped silently is the opposite of a pre-fill: the owner assumes it was handled.

## If candidate cells are ever wanted

Showing "*menn* can be pl. nom./acc. or sg. dat." as a hint would be the owner's own paradigm knowledge replayed, and shows information, not a verdict, which is the shape the automation-bias review favours. It would need a set-valued field and is a new feature, not a fix. Nothing here recommends it. ^[inferred]

## Open Questions

- Should apply set a visible "from remembered" mark on each filled field, or only the derived "needs context" state?
- Does the owner ever remember a meaning? If not, the setting in risk 3 is cheap insurance only.

## Related

- [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ux-recommendations]]
- [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ai-context-policy]]
- [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-current-capabilities]]
- [[synthesis/Research: Qt and Translation Workbench Best Practice]]

## Sources

- [[references/ai-disclosure-and-suggestion-bias-sources]]
- Repo files named in the front matter; the owner's description of their own use.
