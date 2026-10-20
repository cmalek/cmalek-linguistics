---
title: >-
    Desktop UX guidance: Apple, Microsoft, GNOME, NN/g, WCAG and the user's design links
category: references
tags: [ux, desktop-app, design, accessibility, hig]
relationships:
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ux-recommendations]]"
    type: informs
  - target: "[[references/interaction-design-5th-edition]]"
    type: related_to
sources:
  - "https://developer.apple.com/design/human-interface-guidelines/modality"
  - "https://developer.apple.com/design/human-interface-guidelines/undo-and-redo"
  - "https://developer.apple.com/design/human-interface-guidelines/the-menu-bar"
  - "https://developer.apple.com/design/human-interface-guidelines/settings"
  - "https://developer.apple.com/design/human-interface-guidelines/dark-mode"
  - "https://learn.microsoft.com/en-us/windows/win32/uxguide/how-to-design-desktop-ux"
  - "https://developer.gnome.org/hig/patterns/feedback/dialogs.html"
  - "https://www.nngroup.com/articles/modal-nonmodal-dialog/"
  - "https://www.w3.org/WAI/WCAG21/Understanding/character-key-shortcuts"
  - "https://www.w3.org/WAI/WCAG22/Understanding/use-of-color.html"
  - "https://www.zotero.org/support/pdf_reader"
  - "https://help.obsidian.md/plugins/command-palette"
  - "https://appilian.com/native-desktop-ui-ux-design-application-development-a-comprehensive-guide/"
summary: >-
    Rules from primary design guidelines on modality, undo, menus, settings, dark mode, shortcuts and colour, plus what two of the user's three starting links actually offered (Appilian, generic; duitdesign and Dribbble unreadable).
provenance:
  extracted: 0.75
  inferred: 0.15
  ambiguous: 0.10
base_confidence: 0.60
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T22:00:00Z
updated: 2026-10-18T22:00:00Z
---

# Desktop UX guidance: source extract

Read 2026-10-18 by a research subagent. Apple's HIG pages are JavaScript-only; the agent read the JSON that backs each page, which drops inline links. This is a second reading of Apple's text, not a screenshot of the pages.

## The user's starting links

| Source | Result |
|---|---|
| [duitdesign.com article](https://duitdesign.com/how-to-design-a-great-user-experience-for-desktop-applications.html) | Not read: HTTP 403 for three fetch methods. Nothing is claimed about it. |
| [Dribbble tag page](https://dribbble.com/tags/desktop-application) | Not read: a JavaScript gallery that returned no content. No shot was sampled. |
| [Appilian guide](https://appilian.com/native-desktop-ui-ux-design-application-development-a-comprehensive-guide/) | Read about half. Mostly checklists with no cited evidence ("plan accessibility from the beginning"). Concrete items: keep secondary controls hidden until relevant, visible keyboard focus, retained window positions, "Custom components should be introduced only when standard components cannot solve the product requirement". It agrees with the primary guidelines and adds nothing to them. |

## Modality and the annotation dialog

- Apple: "Present content modally only when there's a clear benefit"; keep modal tasks "simple, short, and streamlined"; avoid "an app within your app".
- GNOME: dialogs "obscure the parent window and require a context switch ... inline controls or actions are often preferable"; email composition belongs in the primary window. "Undo is typically a better option than a confirmation dialog."
- NN/g: modals "interrupt the user's workflow" and add a goal, to dismiss them; interruption is justified when work could be lost.
- Reading: the three agree, and the annotation dialog is a frequent narrow task, which is the case they warn about. That applies the guidance to this app and is not a finding about its users. ^[inferred]

## Undo, menus, settings, appearance

- Apple undo: label entries ("Undo Typing"), highlight the result of each undo (scroll to the restored paragraph), and "Avoid placing unnecessary limits on the number of times people can undo or redo".
- Apple menus: "If a menu bar item isn't actionable, disable the action instead of hiding it"; list commands in the menu bar even if available elsewhere. Microsoft: people "rely on an application's menus to discover and learn the available command set"; document accelerators in labels or tooltips.
- Apple settings: "Minimize the number of settings"; put task-specific options in the view they affect; open with Command-Comma. Apple dark mode: "Avoid offering an app-specific appearance setting."
- Microsoft: "the ultimate measure of power is productivity, not the number of features"; "make the hard decision and choose the best [way]" rather than offering all as options. That page is Windows 7 era and says it was not updated.

## Keyboard and colour

- Apple: define custom shortcuts "for only the most frequently used app-specific commands"; support Full Keyboard Access. GNOME: "every action should also be possible with the keyboard". WCAG 2.1.4 (Level A, 2.1 page): character-key shortcuts must be turnable off, remappable, or active only on focus, because they are "easy to accidentally trigger, especially with speech input".
- Apple and WCAG 1.4.1: do not rely on colour alone; add text labels, glyphs or shapes. WCAG 1.4.3 asks 4.5:1 text contrast. The Okabe-Ito palette was read only on a secondary lab page; its original source returned nothing.

## Patterns from comparable tools

- Zotero reader: "locked mode" keeps a highlight tool and colour active, so each selection creates an annotation. Obsidian: a fuzzy command palette lists every command with its shortcut; workspaces save layouts. OmegaT: a pane that signals when it has content for the current segment, plus "Restore OmegaT Window". ELAN: entry limited to a controlled vocabulary through a pull-down. Calibre: a highlights list and keyboard link hints.

## Features to avoid

- Automation bias: Goddard et al. (2011, review of 74 clinical-decision-support studies) found over-reliance falls when systems show "supportive information rather than commands" and less on-screen detail; display prominence raised it. Clinical, not annotation, so the carry-over is an extrapolation. ^[inferred]
- Onboarding: NN/g says tutorials "interrupt users ... and are quickly forgotten"; Apple prefers optional, contextual help. Gamification: one thin secondary page, about employer-mandated settings; weak evidence either way.

## Limits

Not read: Apple Inspectors, GNOME sidebar and split-view pages, every KDE HIG subpage, Scrivener, FLEx and Alpheios docs, NN/g pages on feature creep and expert users. No source was found for synchronised scrolling or "N of M annotated" counters.

## Related

- [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ux-recommendations]]
- [[references/interaction-design-5th-edition]]
- [[concepts/ux-interface-selection]]
- [[skills/ux-prototyping]]
- [[synthesis/Research: Qt and Translation Workbench Best Practice]]

## Sources

- The pages in the front matter, plus NN/g progressive-disclosure and onboarding pages, WCAG contrast pages, GNOME keyboard and placeholder pages, Microsoft keyboard-accelerator pages, the PMC automation-bias review (PMC3240751) and the Calibre, Anki, ELAN and OmegaT manuals.
