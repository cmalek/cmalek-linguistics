---
title: >-
    aenglisc_toolkit: integrating with the operating system
category: concepts
tags: [aenglisc-toolkit, os-integration, macos, windows, linux, packaging]
relationships:
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-current-capabilities]]"
    type: extends
  - target: "[[references/desktop-os-integration-sources]]"
    type: derived_from
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-idiom-plan]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-cross-platform-conventions]]"
    type: related_to
  - target: "[[projects/aenglisc-toolkit/skills/pyside6-deploy-on-6-11]]"
    type: related_to
sources:
  - "[[references/desktop-os-integration-sources]]"
  - "repo:/Users/cmalek/src/personal/aenglisc_toolkit @ 981e093 (ui/theming.py, ui/highlighting.py, ui/sentence_card.py, pyproject.toml)"
  - "user decisions 2026-10-18"
  - "agent:aenglisc-toolkit-session-2026-10-18"
summary: >-
    OS integration for a cross-platform PySide6 app: PDF as the document, System/Light/Dark, and pyside6-deploy. On 6.11.2 the tool reads a spec file, not pyproject.toml.
provenance:
  extracted: 0.35
  inferred: 0.55
  ambiguous: 0.10
base_confidence: 0.45
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T22:30:00Z
updated: 2026-10-20T15:55:46Z
snapshots:
  - "[[_raw/_archived/2026-10-18-pyside6-deploy-spec-only-config|2026-10-18-pyside6-deploy-spec-only-config]]"
---

# aenglisc_toolkit: integrating with the operating system

The target is macOS, Windows 11 and later, and popular Linux distributions; see [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-cross-platform-conventions]] for how to weigh the platforms' guidelines. Source facts and the gap that no Apple page was readable are on [[references/desktop-os-integration-sources]]. Ratings are payoff / effort and are judgement. ^[inferred]

## Decisions recorded 2026-10-18

1. **The document is the exported PDF**, the artifact written from the Full Translation window. Projects stay inside the database. This removes the project-file-type plan and the title-bar file path (the two items that needed a project "file").
2. **Light and dark both stay; System becomes the default.**
3. **Move to `pyside6-deploy`.** Signing is the owner's pain point.

## What follows from the PDF being the document

| Change | Payoff / effort | Notes |
|---|---|---|
| After export, offer "show in folder" and "open the PDF" through `QDesktopServices.openUrl` on the file or folder URL | high / low | Cross-platform through Qt; reveal-and-select variants need per-OS code. |
| Make the PDF self-describing: title, author and language metadata, embedded fonts (þ ð æ ƿ ċ ġ), and the app version, schema version and a content hash from the export manifest | medium-high / low-medium | Metadata through LaTeX `hyperref` options is background knowledge, not checked here. ^[inferred] |
| Consider attaching the project JSON inside the PDF so the artifact can be regenerated | unknown / unknown | A feasibility idea only; no source read on LaTeX file embedding. |
| Native file dialogs for the save path (the default), a remembered last export folder, and a Print command through `QPrintDialog` | medium / low | A Flatpak portal path may not persist, so test the remembered folder. |
| Weigh accessible-PDF output against `reledpar` | low-medium / high | CTAN marks `reledpar`, `paracol` and `expex` "Tagged PDF – incompatible". Matters only if tagged PDF becomes a goal. |

## Theme: System, Light, Dark

The app already has two palette themes (`qt_themes`: Nord for dark, modern light) chosen in Settings and stored as `theme/name`. Adding a third value, `system`, needs three code changes (found 2026-10-18):

1. `ui/theming.py` must resolve `system` to a theme by reading `QGuiApplication.styleHints().colorScheme()` (available since Qt 6.5; the app requires PySide6 6.6 or later) and re-apply on `colorSchemeChanged`.
2. **Two places treat the stored string as the truth about darkness**: `ui/highlighting.py` (twice, `== "dark"`) and `ui/sentence_card.py` (`theme == "dark"`, with a default of `"nord"` that already disagrees with the application default `"dark"`). With a `system` value these would always pick light colours. Derive "is dark" from the palette (window lightness) in one function and call it from all three sites. ^[inferred]
3. The Settings dialog gets a third option and a "System" default for new installs; existing users keep their stored choice.

Qt notes: `setColorScheme` (6.8) is not needed because the app sets its own palette; `colorScheme` may be reported unknown on some Linux desktops, which needs a fallback (background knowledge, not read); and `colorSchemeChanged` fires while "the old palette is still in effect", so apply the new theme from the signal, not from a palette read inside it. ([QStyleHints](https://doc.qt.io/qt-6/qstylehints.html)) The hard-coded highlight colours still need a non-colour cue and checked contrast in both themes ([[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ux-recommendations]]).

## Packaging: `pyside6-deploy`

- Qt for Python recommends it over PyInstaller; it wraps Nuitka and writes `pysidedeploy.spec`. Current docs also describe a `[tool.pyside6.deploy]` table (`title`, `input_file`, `exec_directory`, `icon`, `mode`, `extra_args`, `macos_permissions`). Precedence is CLI, then pyproject, then spec. `pyside6-deploy --init` merges the table into the spec. Machine-derived fields (modules, plugins, packages) stay in the spec. Output is `<name>.app` on macOS and `<name>.dist` on Windows and Linux; the default mode is standalone from Qt 6.12. ([deploy docs](https://doc.qt.io/qtforpython-6/deployment/deployment-pyside6-deploy.html))
- **Installed 6.11.2 does not implement that table.** The copy read on 2026-10-18 takes settings from `pysidedeploy.spec`. `mode` defaults to `onefile`. `pyproject` mentions in `deploy_lib/config.py` are `pyside6-project` lookups, not deploy settings. PyPI's latest then was 6.12.0; that this release contains the documented table was not checked. ^[inferred] Detail: [[projects/aenglisc-toolkit/skills/pyside6-deploy-on-6-11]].
- The tool was not run. A virtualenv created under an older checkout left `.venv/bin/pyside6-deploy` with a shebang for the old interpreter. The venv's Python still ran (3.14, PySide6 6.11.2). Whether Nuitka supports 3.14 was not checked. ^[ambiguous]
- The docs list no signing or notarization option, and the macOS `macdeployqt` flags are C++ tooling. So signing remains a separate step or a skipped one.
- **Consequences of shipping unsigned**, as far as the sources read go: Windows SmartScreen warns for items with no reputation (Microsoft page read); on macOS the Sparkle and PyInstaller pages tie updates and the hardened runtime to notarization, and Apple's own pages were unreadable, so first-run behaviour for an unsigned `.app` is unverified here; Linux packages are usually unsigned (not read). This is the owner's trade-off to make; the sources do not say it is wrong. ^[inferred]
- **Spike before committing:** the app bundles a QtHelp `.qch`/`.qhc`, Tectonic binaries and a TeX bundle, and fonts (`Anvers-Semibold.ttf` case problem on Linux). Whether Nuitka picks up those data files, the build time and the bundle size are not covered by anything read. Keep the PyInstaller spec until a build passes the manual smoke test on all three systems. ^[inferred]

## Other ranked items (unchanged by the decisions)

| Change | Payoff / effort | Notes |
|---|---|---|
| `QStandardPaths` for data and cache; local path on Windows, XDG data on Linux; keep the env override and migrate old folders | high / low | Today's Linux path is `~/.config`. Never exclude the database from backups. |
| Explicit `MenuRole`s and `QKeySequence.StandardKey` everywhere; correct `CFBundleName` | high / low | The `setproctitle` patch may become unnecessary. |
| Remove the `QSystemTrayIcon` welcome balloon | high / low | Use the status bar. |
| Accessible names, non-colour cues, tab order | high / low-medium | Custom-painted views are invisible to screen readers unless they implement accessible interfaces. |
| Custom update check | medium / low | Sparkle has no documented PyInstaller or Nuitka route. |
| Linux metadata (`.desktop`, AppStream) and a Windows installer | medium / low-medium | Part of packaging. |

**Dropped by the PDF decision:** a `.aenglisc` file type with `QFileOpenEvent`, `CFBundleDocumentTypes`, `setWindowFilePath` and `setWindowModified`. Skip Spotlight, Quick Look and Windows shell handlers (native code, impractical from Python).

## Open Questions

- Does a Nuitka build of the app run, with help, Tectonic and fonts working, on all three systems?
- Does `colorScheme()` report Dark and Light correctly on the owner's target Linux desktops?
- Should a PDF carry the manifest hash and an attached project file?

## Related

- [[projects/aenglisc-toolkit/aenglisc-toolkit]]
- [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-roadmap-trello]]
- [[synthesis/Research: Qt and Translation Workbench Best Practice]]

## Sources

- [[references/desktop-os-integration-sources]]
- [[_raw/_archived/2026-10-18-pyside6-deploy-spec-only-config.md]]
