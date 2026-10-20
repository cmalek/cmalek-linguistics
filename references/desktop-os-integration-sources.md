---
title: >-
    Desktop OS integration: Qt, Microsoft, freedesktop and PyInstaller sources
category: references
tags: [qt, os-integration, macos, windows, linux, packaging]
relationships:
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-os-integration]]"
    type: informs
  - target: "[[references/qt-official-docs-best-practice]]"
    type: related_to
sources:
  - "https://doc.qt.io/qt-6/qfileopenevent.html"
  - "https://doc.qt.io/qt-6/qwidget.html"
  - "https://doc.qt.io/qt-6/qstandardpaths.html"
  - "https://doc.qt.io/qt-6/macos-issues.html"
  - "https://doc.qt.io/qt-6/qdesktopservices.html"
  - "https://doc.qt.io/qt-6/accessible.html"
  - "https://pyinstaller.org/en/stable/feature-notes.html"
  - "https://learn.microsoft.com/en-us/windows/win32/shell/fa-file-types"
  - "https://specifications.freedesktop.org/basedir-spec/latest/"
  - "https://specifications.freedesktop.org/shared-mime-info-spec/latest/ar01s02.html"
  - "https://docs.flatpak.org/en/latest/sandbox-permissions.html"
  - "https://sparkle-project.org/documentation/"
summary: >-
    Primary-source facts for document handling, data paths, colour scheme, menu roles, accessibility, notifications and signing in a Qt app. No Apple developer page could be read; Apple-only points are marked unverified.
provenance:
  extracted: 0.65
  inferred: 0.20
  ambiguous: 0.15
base_confidence: 0.55
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T22:00:00Z
updated: 2026-10-18T22:00:00Z
---

# Desktop OS integration: source extract

Read 2026-10-18 by a research subagent. **Every `developer.apple.com` page came back empty** (JavaScript-rendered) and WebFetch gave 404s, so no Apple primary source was read for this topic. Apple behaviour appears below only where Qt, PyInstaller or Sparkle documentation describes it, or is tagged *unverified*. The Qt pages are the C++ reference; PySide6 availability is inferred in each case.

## Document handling

- macOS window icons "will not be displayed unless a file path has also been set using setWindowFilePath". `setWindowModified(True)` needs a `[*]` placeholder in the window title. ([QWidget](https://doc.qt.io/qt-6/qwidget.html))
- Double-click in Finder or a drop on the Dock arrives as a `QFileOpenEvent` on the application, but only if the bundle declares its types (`CFBundleDocumentTypes` with `LSItemContentTypes`). Use `url()` and `isLocalFile()`, since `file()` "is not guaranteed to be the name of a local file". ([QFileOpenEvent](https://doc.qt.io/qt-6/qfileopenevent.html))
- PyInstaller advises against argv emulation with UI toolkits; handle the event instead, and add the plist keys through `info_plist=` in `BUNDLE()`. The first event can arrive before the window exists, so queue it. ([feature notes](https://pyinstaller.org/en/stable/feature-notes.html))
- Windows: extension keys live under `HKEY_CLASSES_ROOT` with a ProgID; call `SHChangeNotify` after changing associations; private extensions are "not prone to conflicts"; `SHAddToRecentDocs` feeds recent items and Jump Lists. A custom Jump List needs COM and is not shown to be practical from Python. ([file types](https://learn.microsoft.com/en-us/windows/win32/shell/fa-file-types))
- Linux: ship a MIME XML under `packages/`, run `update-mime-database`, and list `MimeType` in the `.desktop` file. The XDG recent-file spec returned empty and was not read.
- Save, Revert and Versions are AppKit `NSDocument` features that Qt Widgets does not supply. *Unverified.*

## Locations

- `AppDataLocation` returns the roaming path on Windows; `AppLocalDataLocation` is the local path there and equals `AppDataLocation` elsewhere. macOS: `~/Library/Application Support/<APPNAME>`; Linux: `~/.local/share/<APPNAME>`. Qt lists `AppConfigLocation` as `~/Library/Preferences/<APPNAME>` on macOS. A sandboxed macOS app has `~` redirected into `~/Library/Containers/<BUNDLE-ID>/Data`. ([QStandardPaths](https://doc.qt.io/qt-6/qstandardpaths.html))
- XDG has a state directory (`$XDG_STATE_HOME`) for logs and recent history. ([basedir spec](https://specifications.freedesktop.org/basedir-spec/latest/))
- Choosing the local path for a large SQLite file on Windows is the subagent's reasoning, not a Qt statement. ^[inferred]
- Time Machine exclusion flags and the `Preferences` guidance are Apple topics and unverified.

## Look and behaviour

- `QStyleHints.colorScheme` and `colorSchemeChanged` (6.5); `setColorScheme` (6.8). Qt "won't overwrite palette entries that have been explicitly set by the application". No accent-colour property on that page.
- Qt turns menu bars into native macOS menu bars; `MenuRole` values (`AboutRole`, `PreferencesRole`, `QuitRole`) apply only to actions in a top-level menu and must be set before the action joins the bar. The About text uses the application name from `Info.plist`, so a correct `CFBundleName` is the real fix for the menu name that `setproctitle` patches. ([macOS issues](https://doc.qt.io/qt-6/macos-issues.html)) ^[inferred]
- `QKeySequence.StandardKey` maps Open, Save, Find, Preferences, Quit per platform. `QFileDialog` is native by default. `QDesktopServices.setUrlHandler` handles a custom scheme in-app; OS registration is separate.

## Accessibility

- "Do not depend on colors only to provide information." Standard Qt widgets expose accessibility to VoiceOver, NVDA and Orca; custom-painted widgets need `QAccessibleInterface` implementations, and no page was found on doing that from PySide6. ([accessible](https://doc.qt.io/qt-6/accessible.html))
- WCAG 1.4.1: colour must not be "the only visual means of conveying information". `QAccessibilityHints.contrastPreference` is Qt 6.10 and `motionPreference` is Qt 6.12, so check the shipped PySide6 version.

## Notifications and progress

- `QSystemTrayIcon.showMessage` works but the page does not describe macOS rendering or bundle requirements. A removed `QWinTaskbarProgress` in Qt 6 came from a search summary, not a fetched page. Dock badges and taskbar progress from Python are unconfirmed.

## Distribution and trust

- PyInstaller signs ad hoc by default; `--codesign-identity` enables the hardened runtime and "will not work with self-signed certificates"; `universal2` needs both slices in every binary. Sparkle expects notarization and EdDSA-signed archives. Windows SmartScreen warns on files with no reputation. ([Sparkle](https://sparkle-project.org/documentation/))
- Flatpak portals grant file access when the user picks a path in the native chooser, and Qt "implement[s] transparent support" for them. The chosen path is a portal path, so a remembered "last export folder" may not survive. ([Flatpak](https://docs.flatpak.org/en/latest/sandbox-permissions.html)) ^[inferred]
- AppStream needs `id`, `name` and `summary`.

## Not covered

Apple HIG and developer docs, Core Spotlight, Quick Look, NSSpellChecker, UNUserNotificationCenter, GNOME and KDE HIG pages on OS integration, Windows toast and code-signing pages, Qt WebEngine spellcheck, drag-and-drop, the Services menu, the Mac and Microsoft Stores, Snap.

## Related

- [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-os-integration]]
- [[references/qt-official-docs-best-practice]]
- [[synthesis/Research: Qt and Translation Workbench Best Practice]]

## Sources

- The Qt, Microsoft, freedesktop, Flatpak, PyInstaller and Sparkle pages in the front matter.
