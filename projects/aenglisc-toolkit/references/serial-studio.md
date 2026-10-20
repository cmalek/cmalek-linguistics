---
title: >-
  Serial Studio
category: references
tags: [qt, qml, dashboard, design]
sources:
  - "url:https://github.com/Serial-Studio/Serial-Studio"
summary: >-
  Serial Studio: Qt telemetry dashboard where a project file defines the data format and widgets; GPL build plus a paid Pro tier.
provenance:
  extracted: 0.71
  inferred: 0.14
  ambiguous: 0.14
base_confidence: 0.47
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: peripheral
created: 2026-10-18T18:08:40Z
updated: 2026-10-18T18:08:40Z
snapshots:
  - "[[_raw/_archived/GITHUB Serial-Studio 2026-10-17|GITHUB Serial-Studio 2026-10-17]]"
---

# Serial Studio

Serial Studio turns hardware data (serial, Bluetooth LE, network sockets; industrial buses in Pro) into a live dashboard. Clipped at 7.2k stars; C 46.4%, C++ 33.2%, QML 4.2%.

## Key Points

- Three modes: project file (recommended; groups, datasets and widgets defined in a form-based Project Editor), Quick Plot (CSV lines drawn immediately), and console only.
- Frame parsers come as built-in configured templates (the default), JavaScript, or Lua.
- Automation: a TCP API on port 7777 with 360+ commands, a gRPC server on port 8888, and an MCP server over the same command set.
- Records to CSV in the GPL build; MDF4, SQLite session recording and PDF reports are Pro. An AI assistant that edits the project is Pro and uses a bring-your-own key.
- The widget count is stated inconsistently inside the README (17 in one section, 23 in another), and some widgets are Pro. ^[ambiguous]
- Distribution: Windows, macOS (universal DMG, Homebrew cask), Linux (AppImage, Flatpak, DEB, RPM), Raspberry Pi ARM64.
- Relevance to [[projects/aenglisc-toolkit/aenglisc-toolkit|aenglisc_toolkit]]: a declarative project file driving the UI is a pattern for configuring annotation views. ^[inferred]

Part of [[projects/aenglisc-toolkit/concepts/qt-app-design-references|Qt app design references]].

## Sources

- [[_raw/_archived/GITHUB Serial-Studio 2026-10-17]] — clipping of https://github.com/Serial-Studio/Serial-Studio (2026-10-17)
