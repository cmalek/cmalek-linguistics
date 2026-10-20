---
title: >-
    aenglisc_toolkit: where AI context may and may not appear
category: concepts
tags: [aenglisc-toolkit, ai, policy, provenance, translation]
relationships:
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-intent]]"
    type: extends
  - target: "[[references/ai-disclosure-and-suggestion-bias-sources]]"
    type: derived_from
  - target: "[[concepts/manual-translation-workbench-features]]"
    type: related_to
sources:
  - "[[references/ai-disclosure-and-suggestion-bias-sources]]"
  - "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-intent]]"
summary: >-
    A boundary for AI help in a translation tool that must never translate: context only, pulled by the user, labelled, kept out of annotation fields and out of exports unless cited. Evidence for the bias risk is thin.
provenance:
  extracted: 0.15
  inferred: 0.75
  ambiguous: 0.10
base_confidence: 0.40
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T22:30:00Z
updated: 2026-10-18T22:30:00Z
---

# aenglisc_toolkit: where AI context may and may not appear

**Status, decided 2026-10-18: no AI context in the next release.** The app has already shipped several releases without any AI, so this is a deferral, not a removal. The rest of this page is a proposal to keep for if the question comes back.

The user's rule: no AI for translation anywhere in the app; AI for context about the text is acceptable. The product intent already says the translator makes every linguistic decision ([[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-intent]]). This page turns that into a testable boundary. It is a proposal drawn from [[references/ai-disclosure-and-suggestion-bias-sources]], not a requirement from any source.

## The line

| Allowed (context) | Not allowed |
|---|---|
| Background on the work, author, date, manuscript, historical setting | Any suggested Modern English rendering, gloss, sense or paraphrase of the text |
| Pointers to parallel passages, cited scholarship, dictionary entries for the user to read | Suggested POS, case, root or lemma for a token |
| Explaining a grammar term or poetic convention | Pre-filled annotation, translation or confidence fields |
| Summarising a commentary the user supplies | Ranking or "best guess" among senses |

Context that merely restates a translation in other words is translation, so the check is on content, not on where in the UI it appears. Rendering a line "in modern terms" fails the table even if labelled as context. ^[inferred]

## Interface rules

1. **Pull, not push.** The user asks; nothing appears beside a token or sentence unprompted.
2. **Separate surface.** Context lives in its own pane or dialog and never writes to an annotation, note or translation field. Copying text into a note is a deliberate user act, and the pasted note keeps the label.
3. **Persistent label.** Every AI-produced item shows "AI context", the model name and version, the date and the prompt, matching the element lists in MLA and Chicago. ([[references/ai-disclosure-and-suggestion-bias-sources]])
4. **Not in exports by default.** Include it only on an explicit opt-in, rendered as a cited note and never as the translator's words. COPE says the tool cannot be an author and its use must be disclosed.
5. **Sourced candidates over answers.** Where context could shade into suggestion, show the underlying evidence (dictionary entry, passage) and not a conclusion. The automation-bias review favours "supportive information rather than commands". ^[inferred]
6. **Confidence and senses stay human.** Never pre-fill them.
7. **Hidden by default.** Off until the user turns the feature on, with a visible state indicator.

## Evidence strength

The risk that suggestions anchor translators rests on one MT post-editing study (bias errors, mostly terminology and polysemy, which is exactly what sense-per-token work involves) and a clinical review; a CHI study found post-editing improved quality. None tests a pull-only context pane, and no study of reading-with-lookup tools was found. So the rules above are cautious design, not a demonstrated necessity. ^[inferred]

## The existing risk is not AI

Remembered-annotation propagation fills fields from the user's own past judgment. The owner stores only what is known on sight, so it is not the anchoring case, with one exception (a stored meaning). See [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-remembered-annotations-and-bias]].

## Open Questions

- Does the user want any AI context at all in the first release? The safest first version has none.
- Where should the prompt text live, given it may contain the source line? A local-only provider would avoid sending text off the machine.
- Do any publishers the user targets set rules beyond COPE, MLA and Chicago?

## Related

- [[projects/aenglisc-toolkit/aenglisc-toolkit]]
- [[concepts/manual-translation-workbench-features]]
- [[synthesis/Research: Qt and Translation Workbench Best Practice]]

## Sources

- [[references/ai-disclosure-and-suggestion-bias-sources]]
- [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-intent]]
