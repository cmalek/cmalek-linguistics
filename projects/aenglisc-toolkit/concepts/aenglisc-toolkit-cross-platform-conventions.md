---
title: >-
    aenglisc_toolkit: following platform conventions on macOS, Windows 11 and Linux
category: concepts
tags: [aenglisc-toolkit, cross-platform, ux, conventions, qt]
relationships:
  - target: "[[references/desktop-ux-guidelines-sources]]"
    type: derived_from
  - target: "[[references/desktop-os-integration-sources]]"
    type: derived_from
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-os-integration]]"
    type: related_to
sources:
  - "[[references/desktop-ux-guidelines-sources]]"
  - "[[references/desktop-os-integration-sources]]"
  - "[[references/qt-official-docs-best-practice]]"
  - "user statement 2026-10-18: target macOS, Windows 11+ and popular Linux"
summary: >-
    A rule for using Apple, Microsoft and GNOME guidance together: adopt what two or more agree on or what Qt abstracts, and treat single-platform items as optional polish; a table of which guideline said what.
provenance:
  extracted: 0.35
  inferred: 0.55
  ambiguous: 0.10
base_confidence: 0.50
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T23:30:00Z
updated: 2026-10-18T23:30:00Z
---

# aenglisc_toolkit: following platform conventions on macOS, Windows 11 and Linux

The owner agrees with Apple's guidance but wants one app on macOS, Windows 11 and later, and popular Linux distributions. The strongest sources read were Apple's, simply because they were the most readable; that is a bias of the evidence, not of the platforms. The rule below is a proposal from the vault, not from any source. ^[inferred]

## Rule

1. **Adopt** a recommendation when at least two of the three vendors' guidelines say it, or when Qt provides a per-platform abstraction for it (`QKeySequence.StandardKey`, `MenuRole`, `QStandardPaths`, native file dialogs, palette-based colour). Qt then does the platform translation.
2. **Treat as optional polish** anything only one vendor says and Qt does not abstract. Do it behind a call that costs nothing elsewhere, and never at the expense of another platform.
3. **Don't invent** platform behaviour from memory. Where a cell below says "not read", the claim is unsupported.

## Which guideline said what

| Topic | Apple HIG | Microsoft | GNOME | Action |
|---|---|---|---|---|
| Modals for frequent tasks | modal only with clear benefit; keep short | dialogs "disrupt"; reserve for must-read, destructive, blocking | inline preferred; undo over confirmation | **Adopt** (3 of 3): prototype inline editing |
| Keyboard | few custom shortcuts; Full Keyboard Access | accelerators for common actions, shown in labels/tooltips | every action by keyboard; Ctrl+letter; avoid Alt | **Adopt**; use `StandardKey` |
| Menus | same items always, disabled not hidden | people learn commands from menus | menu bar page not read | **Adopt** menu bar with disabled-not-hidden; check GNOME separately |
| Undo | named steps, no needless limit, show the result | not read | prefer undo to confirmation | Adopt via `QUndoStack` |
| Preferences | Command-Comma, minimise settings | not read | not read | `StandardKey.Preferences` plus `PreferencesRole`; placement on Windows/Linux not sourced |
| Appearance | follow the system, avoid an app-specific setting | not read | not read | See the theme decision below |
| Colour alone | add labels or shapes | not read here (WCAG covers it) | not read | **Adopt** (Apple + WCAG + Qt) |
| Onboarding | optional, contextual | not read | placeholders with guidance | Adopt contextual help |

The Apple-only items (proxy icon, edited dot, Dock, Services, Spotlight, Quick Look) are optional polish by rule 2. The Windows-only items (Jump Lists, taskbar progress) likewise.

## Decisions recorded 2026-10-18

- **Theme.** Keep Light and Dark (users depend on both), add **System** as the default, and re-apply on `colorSchemeChanged`. Apple's "avoid an app-specific appearance setting" is satisfied by defaulting to System; the explicit Light/Dark choice stays because users want it. See [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-os-integration]] for the three code places that must change.
- **Deployment.** Move to `pyside6-deploy`; signing is the owner's pain point. Consequences are listed on the OS-integration page.

## Open Questions

- What do Microsoft's and GNOME's pages say about appearance, preferences placement and menu bars? They were not read or returned empty.
- Does the Linux build target GNOME, KDE or both? Qt follows the platform theme only as far as the platform plugin allows; not researched.

## Related

- [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ux-recommendations]]
- [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-os-integration]]
- [[synthesis/Research: Qt and Translation Workbench Best Practice]]

## Sources

- [[references/desktop-ux-guidelines-sources]]
- [[references/desktop-os-integration-sources]]
