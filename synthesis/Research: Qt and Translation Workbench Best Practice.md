---
title: >-
    Research: Qt and Translation Workbench Best Practice
category: synthesis
tags: [qt, pyside6, translation, ux, os-integration, aenglisc-toolkit, research]
relationships:
  - target: "[[projects/aenglisc-toolkit/aenglisc-toolkit]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-idiom-plan]]"
    type: derived_from
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ux-recommendations]]"
    type: derived_from
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-academic-output-plan]]"
    type: derived_from
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-os-integration]]"
    type: derived_from
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ai-context-policy]]"
    type: derived_from
sources:
  - "[[references/qt-official-docs-best-practice]]"
  - "[[references/desktop-os-integration-sources]]"
  - "[[references/desktop-ux-guidelines-sources]]"
  - "[[references/translation-tools-and-scholarly-editing-standards]]"
  - "[[references/ai-disclosure-and-suggestion-bias-sources]]"
  - "[[references/beginning-pyqt-willman-2022]]"
  - "[[references/interaction-design-5th-edition]]"
  - "agent:aenglisc-toolkit-session-2026-10-18"
summary: >-
    Four parallel research passes on Qt practice, OS integration, desktop UX and translation-tool standards, applied to aenglisc_toolkit: stock Qt replaces hand-rolled undo, threads and styles; output needs per-gloss sources; AI stays context-only.
provenance:
  extracted: 0.40
  inferred: 0.52
  ambiguous: 0.08
base_confidence: 0.55
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: core
created: 2026-10-18T22:45:00Z
updated: 2026-10-20T15:55:46Z
snapshots:
  - "[[_raw/_archived/2026-10-18-pyside6-deploy-spec-only-config|2026-10-18-pyside6-deploy-spec-only-config]]"
  - "[[_raw/_archived/2026-10-18-qt-offscreen-no-x11|2026-10-18-qt-offscreen-no-x11]]"
---

# Research: Qt and Translation Workbench Best Practice

## Overview

Four independent research passes (Qt documentation, OS integration, desktop UX guidance, translation and scholarly-editing tools) were run on 2026-10-18 on top of the existing aenglisc_toolkit baseline ([[projects/aenglisc-toolkit/aenglisc-toolkit]]), which already records capabilities, architecture and verified gaps. One round of search plus fetch per pass, with no second gap-fill round and no separate contradiction round; the passes were parallel and reported by subagents, so every source was read through an intermediary. The `base_confidence` of 0.55 sits below the formula's result because of the gaps listed below. The request's "non-idomatic/DIY" is read as *replace hand-rolled code with stock Qt*.

## Key Findings

- **Three hand-built parts are the clearest targets, and the docs support all three.** Undo: `QUndoStack` merges commands by id, has an unlimited default, and names the next step; Apple's undo guidance says avoid limits and scroll to the change. Threads: widgets are main-thread only, `QProcess` is the async route for Tectonic, and a lambda connected to a worker signal runs in the worker thread. Styling: Qt calls style sheets "a tool for prototyping and for small, local adjustments" and says not to switch themes with them. ([[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-idiom-plan]], [[references/qt-official-docs-best-practice]])
- **The annotation modal conflicts with three independent guidelines.** Apple, GNOME and NN/g all steer frequent narrow tasks away from modals. An editable details sidebar and a Zotero-style sticky mode are the candidate replacements, to be prototyped, not assumed. ([[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ux-recommendations]])
- **Colour-only highlighting and bare-letter shortcuts are the two accessibility gaps** the sources agree on (Apple HIG, Qt, WCAG 1.4.1 and 2.1.4). ([[references/desktop-ux-guidelines-sources]])
- **Academic output needs provenance more than formats.** The annotation model stores no source for a gloss; Bosworth-Toller's own citation shows the minimum record. TEI is the reuse format; Leipzig labels and `reledmac` note series suit the PDF. ([[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-academic-output-plan]])
- **The CAT-tool features worth copying are the ones that surface the translator's own work**: a glossary pane lit for the current sentence, a consistency check, sentence status. The ones to skip write candidates into the target. ([[concepts/manual-translation-workbench-features]])
- **AI help fits as pulled, labelled, separate context only.** COPE, MLA and Chicago all require disclosure; the case that suggestions bias translators is real but thin. ([[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ai-context-policy]])
- **OS integration payoff is in the low-effort basics**: standard paths, system colour scheme, menu roles, dropping the tray balloon, a project file type, and signing. ([[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-os-integration]])

## Cross-cutting Insight

Remembered-annotation propagation sits at the junction of three results: it is manual-safe by the tool test, it is the nearest feature to fuzzy translation-memory fill, and it carries no source record. The first draft proposed marking reused annotations unreviewed. The owner's description of their use (store only what is certain on sight, leave ambiguous cells such as *menn*'s case open) changes that: the entries are the translator's own partial judgment, and the real gaps are a partial token that looks finished and a stored meaning that would be a pre-filled gloss. ([[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-remembered-annotations-and-bias]]) ^[inferred]

## Decisions by the owner, 2026-10-18

- **The document is the exported PDF**, not a project file; projects stay in the database. This replaces the project-file-type plan in the OS-integration page.
- **No AI context in the next release.** The proposal page is kept as a deferred note.
- **System, Light and Dark themes, with System as default.** Three code sites read the stored string to decide darkness and need one palette-based function.
- **Move to `pyside6-deploy`**; signing is a known pain point, and the consequences are on the OS-integration page.
- **Target:** macOS, Windows 11 and later, popular Linux. Platform guidance is weighed by the rule on [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-cross-platform-conventions]].

## Core Concepts

- [[concepts/manual-translation-workbench-features]]: which features fit a manual translator.
- [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-idiom-plan]], [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ux-recommendations]], [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-academic-output-plan]], [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-os-integration]], [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ai-context-policy]].

## Entities & Tools

- [[entities/omegat]]: panes and glossary to borrow, TM auto-insert to skip.
- [[entities/tei-p5-guidelines]]: the scholarly export target.
- [[entities/junicode]], [[entities/bosworth-toller]]: existing pages relevant to output.

## Contradictions & Open Questions

- **Dark mode: resolved by decision.** Apple says avoid an app-specific appearance setting; users need both themes. System as default with explicit Light and Dark satisfies both.
- **Shortcuts and palettes.** Microsoft asks for the one best path, Obsidian offers a palette over menus; they differ on redundancy. ^[ambiguous]
- **Deployment: decided to move to `pyside6-deploy`** (no signing option documented; its PyInstaller page says Qt 6 is unsupported, which its own index contradicts). Not yet tested on this app. On the installed PySide6 6.11.2, the tool reads `pysidedeploy.spec`, not the `[tool.pyside6.deploy]` table in the current docs. See [[projects/aenglisc-toolkit/skills/pyside6-deploy-on-6-11]].
- **Offscreen testing.** Qt Test says fully supported "only on X11". On macOS with `DISPLAY` unset, `QT_QPA_PLATFORM=offscreen` in `conftest.py` reported platform `offscreen` and two test files passed. Linux and Windows are still unverified. See [[projects/aenglisc-toolkit/skills/pytest-qt-offscreen-macos]]. ^[ambiguous]
- **Suggestion bias.** Picinini and Ueffing found bias errors; Green et al. found post-editing improved quality. Different settings, no test of a context-only pane.
- **Open:** Does a docked editor handle the full POS form? What is a "document" (export file or database per project)? Which dictionary should the glossary cite? How do real Old English facing-page editions lay out notes?

## Evidence gaps

- **Apple.** No `developer.apple.com` page was readable for OS integration; the HIG was read through its backing JSON, which drops inline links. Apple-only claims are marked unverified.
- **User's starting links.** duitdesign.com (HTTP 403) and the Dribbble tag page (empty) could not be read; the Appilian guide was read about half and is generic checklist advice. Nothing is claimed about the first two.
- **Edition conventions.** DOE and publisher pages were blocked or not found. A follow-up with `paper-search` found one open-access research edition and it was read in part ([[references/mertens-2020-old-english-lives-of-st-martin]]); Dumbarton Oaks and student-edition conventions are still only from review summaries. "What reads as academic" now rests on one edition plus inference.
- **PySide6.** Most Qt pages are the C++ reference; PySide6 names are confirmed only where noted on [[references/qt-official-docs-best-practice]].
- **No code was run, no app was profiled, and no user was observed.** The vault's Interaction Design notes say design claims need an evaluation ([[skills/ux-evaluation-planning]]).
- **Scratch.** Fetched pages are in the session scratchpad only, not archived in the vault.

## Sources Consulted

- [[references/qt-official-docs-best-practice]]
- [[references/desktop-os-integration-sources]]
- [[references/desktop-ux-guidelines-sources]]
- [[references/translation-tools-and-scholarly-editing-standards]]
- [[references/ai-disclosure-and-suggestion-bias-sources]]
- [[references/mertens-2020-old-english-lives-of-st-martin]] (added in the follow-up)
- Vault inputs: [[references/beginning-pyqt-willman-2022]], [[references/interaction-design-5th-edition]], [[projects/aenglisc-toolkit/concepts/qt-app-design-references]], [[references/fincept-terminal-qt-architecture]], and the aenglisc_toolkit baseline pages.
- [[_raw/_archived/2026-10-18-qt-offscreen-no-x11.md]]
- [[_raw/_archived/2026-10-18-pyside6-deploy-spec-only-config.md]]
