---
title: >-
    Qt 6 and Qt for Python official documentation: best-practice extract
category: references
tags: [qt, pyside6, best-practice, documentation]
relationships:
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-idiom-plan]]"
    type: informs
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-practice-gap-analysis]]"
    type: extends
  - target: "[[references/beginning-pyqt-willman-2022]]"
    type: related_to
sources:
  - "https://doc.qt.io/qtforpython-6/"
  - "https://doc.qt.io/qt-6/threads-technologies.html"
  - "https://doc.qt.io/qt-6/threads-qobject.html"
  - "https://doc.qt.io/qt-6/qthread.html"
  - "https://doc.qt.io/qt-6/qprocess.html"
  - "https://doc.qt.io/qt-6/qundostack.html"
  - "https://doc.qt.io/qt-6/qundocommand.html"
  - "https://doc.qt.io/qt-6/qtwidgets-styling-approaches.html"
  - "https://doc.qt.io/qt-6/stylesheet.html"
  - "https://doc.qt.io/qt-6/qstylehints.html"
  - "https://doc.qt.io/qt-6/model-view-programming.html"
  - "https://doc.qt.io/qt-6/qmainwindow.html"
  - "https://doc.qt.io/qt-6/qlockfile.html"
  - "https://doc.qt.io/qtforpython-6/tutorials/basictutorial/signals_and_slots.html"
  - "https://doc.qt.io/qtforpython-6/PySide6/QtTest/index.html"
  - "https://pytest-qt.readthedocs.io/en/latest/"
  - "https://doc.qt.io/qtforpython-6/deployment/deployment-pyside6-deploy.html"
  - "agent:aenglisc-toolkit-session-2026-10-18"
summary: >-
    What the official Qt 6 and Qt for Python pages say about threads, undo, model/view, main windows, styling, signals, testing and deployment, with a macOS offscreen run and a 6.11.2 deploy-spec check.
provenance:
  extracted: 0.78
  inferred: 0.16
  ambiguous: 0.06
base_confidence: 0.62
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T22:00:00Z
updated: 2026-10-20T15:55:46Z
snapshots:
  - "[[_raw/_archived/2026-10-18-pyside6-deploy-spec-only-config|2026-10-18-pyside6-deploy-spec-only-config]]"
  - "[[_raw/_archived/2026-10-18-qt-offscreen-no-x11|2026-10-18-qt-offscreen-no-x11]]"
---

# Qt 6 and Qt for Python documentation: best-practice extract

Read on 2026-10-18 by a research subagent with `defuddle`, then summarised here. Most pages are the C++ reference; PySide6 availability is confirmed only where noted. Nothing was run. Some pages were skimmed, not read in full: the `fetchmore`, `undoframework` and `syntaxhighlighter` examples, `QThreadPool`, QtConcurrent.

## Threads and processes

- Widgets are main-thread only: "the GUI classes, notably QWidget and all its subclasses, are not reentrant. They can only be used from the main thread." Signal emission from a worker is thread-safe. ([threads-qobject](https://doc.qt.io/qt-6/threads-qobject.html))
- Three patterns, by use case: `QRunnable` on the global `QThreadPool` for a one-shot task with progress by signal; a worker `QObject` moved to a `QThread` for a long-lived worker; `QtConcurrent::run` for an existing function, which "cannot be paused, resumed, cancelled or queried for progress". ([threads-technologies](https://doc.qt.io/qt-6/threads-technologies.html))
- Do not add slots to a subclassed `QThread`; use the worker-object recipe (`moveToThread`, `finished` to `deleteLater`, `quit()` then `wait()`). Cancel cooperatively with `requestInterruption()` and `isInterruptionRequested()`. `terminate()` is "dangerous and discouraged". ([qthread](https://doc.qt.io/qt-6/qthread.html))
- A `QObject` with a parent cannot be moved to another thread, and a child must be created in its parent's thread.
- `QProcess` is the asynchronous route for an external tool: `start()`, then `finished`, `errorOccurred` and the `readyRead*` signals; `waitFor*` blocks and must not run on the GUI thread. Pass an absolute program path and keep untrusted arguments away from `.bat`, `.cmd` and `sh -c`. ([qprocess](https://doc.qt.io/qt-6/qprocess.html))
- `QProgressDialog` shows itself only if the estimated time exceeds `minimumDuration` (default 4 s) and reports cancel through `wasCanceled()`.
- PySide6: "For non-Slot type receivers, the code is then executed in the sender's thread context." A lambda connected to a worker signal therefore runs in the worker thread; connect to a `@Slot` method on a GUI object. ([signals and slots](https://doc.qt.io/qtforpython-6/tutorials/basictutorial/signals_and_slots.html))
- `QRunnable` is not a `QObject` and cannot declare signals, so progress needs a small `QObject` helper. The docs imply this; no page states it. A SQLAlchemy session per task, with plain data or IDs returned by signal, is general knowledge and not from Qt. ^[inferred]

## Undo

- `QUndoStack` provides "undo and redo actions, command compression, command macros, and ... a clean state". Merge happens only between commands with the same non-negative `id()`, via `mergeWith()`. `beginMacro`/`endMacro` group steps, and a macro counts as one command toward `undoLimit`. ([qundostack](https://doc.qt.io/qt-6/qundostack.html), [qundocommand](https://doc.qt.io/qt-6/qundocommand.html))
- `undoLimit` defaults to 0, "no limit", and can be set only while the stack is empty. `createUndoAction` and `createRedoAction` return actions whose text follows the next command's `text()`. `setClean()` and `cleanChanged` suit a save indicator.
- PySide6 puts `QUndoStack` and `QUndoCommand` in `QtGui`, not `QtWidgets`. Python lifetime behaviour after `push()` is unconfirmed.
- `QTextDocument` keeps its own undo history; a run of typing in one block is one step, and `setPlainText`/`setHtml` clear it. `QTextCursor.beginEditBlock()` makes grouped edits one step. No page says how to combine it with a `QUndoStack`; giving the text widget `setUndoRedoEnabled(False)` and pushing your own commands is an inference. ^[inferred]

## Model/view and large content

- Convenience widgets (`QListWidget` and kin) are "less flexible"; Qt recommends model/view "unless you strongly need an item-based set of classes". Use `QStyledItemDelegate` as the delegate base. ([model-view-programming](https://doc.qt.io/qt-6/model-view-programming.html))
- Scaling tools: `uniformItemSizes`, `layoutMode = Batched`, `canFetchMore`/`fetchMore`, and `QSortFilterProxyModel`, which transforms a source model "without duplicating the data in memory".
- `QPlainTextEdit` is "optimized to handle large documents" because its layout drops tables, frames and pixel-exact heights. No page quantifies the cost of one widget per item, and none confirms that one `QTextDocument` can safely back several views. ^[ambiguous]

## Main window, settings, single instance

- `saveState`/`restoreState(version)` identify toolbars and docks by `objectName`, which must be unique; a version mismatch returns false and changes nothing. `saveGeometry`/`restoreGeometry` pull an off-screen window back on screen. Wayland generally does not report window position. ([qmainwindow](https://doc.qt.io/qt-6/qmainwindow.html))
- A `QAction` needs to be added to a widget before its shortcut works; `menuRole` applies only to actions in a top-level menu. `QSettings` writes the registry on Windows, plists on macOS and INI files on Unix, and may need `sync()`.
- `QLockFile`: for a long-held resource, call `setStaleLockTime(0ms)` and `tryLock()` with a short timeout, then warn the user. `getLockInfo()` gives pid, host and app name. Stale-lock detection is fallible. ([qlockfile](https://doc.qt.io/qt-6/qlockfile.html))

## Styling

- "Style sheets are a tool for prototyping and for small, local adjustments; for the production look of an application, implement a QStyle". Every `setStyleSheet` repolishes the widget and its children; "Don't assemble style sheets from C++ strings"; "Don't hard-code colors ... Use palette(window), palette(text)". ([styling approaches](https://doc.qt.io/qt-6/qtwidgets-styling-approaches.html), [stylesheet](https://doc.qt.io/qt-6/stylesheet.html))
- Do not switch themes at runtime with `setStyleSheet`. Use a different `QPalette` on the same style for light and dark; Fusion draws from palette roles.
- `QStyleHints.colorScheme` (6.5) follows the system; `setColorScheme`/`unsetColorScheme` (6.8) override it, "not supported on all platforms". During `colorSchemeChanged` "the old palette is still in effect"; app colours update on `PaletteChange`. PySide6 exposes all four names. ([qstylehints](https://doc.qt.io/qt-6/qstylehints.html))
- Rich-text tools for annotated text: `QTextCharFormat` anchors and tooltips, `setExtraSelections` for temporary marks, `QSyntaxHighlighter` with block state, `QTextBlockUserData`. `defaultStyleSheet` affects only HTML inserted afterwards.

## Signals, slots, forms

- PySide6: "We recommend marking all methods used by signal connections with a @Slot decorator"; avoid `__private` methods as receivers; overloaded signals are "not recommended for new code". The fetched PySide6 pages say nothing about lambda lifetime, so that trap is not confirmed here. ^[ambiguous]
- `QDataWidgetMapper` maps form widgets to sections of an item model. Both Qt Widgets and Qt Quick can build text editors; the current Qt page no longer favours Widgets outright. ([topics-ui](https://doc.qt.io/qt-6/topics-ui.html))

## Testing

- PySide6 `QtTest` exposes `QSignalSpy`, `QAbstractItemModelTester` and `QTest`, and says to use pytest for ordinary unit tests. `QAbstractItemModelTester` re-checks a custom model on every change.
- pytest-qt: prefer widget methods to synthetic `qtbot` key and mouse events, which "make the test unreliable and flaky". PySide6 6.5.2+ re-raises event-loop exceptions itself.
- Offscreen: the Qt Test page says the `offscreen` plugin is "only fully supported on X11"; pytest-qt suggests `QT_QPA_PLATFORM=offscreen` for CI anyway. On macOS, with `DISPLAY` unset, aenglisc_toolkit's `conftest.py` sets that variable before importing PySide6, `QApplication.platformName()` returned `offscreen`, and two `qtbot` files passed 45 tests. XQuartz was installed and unused. Linux and Windows were not run. See [[projects/aenglisc-toolkit/skills/pytest-qt-offscreen-macos]]. ^[ambiguous]

## Deployment

- Qt for Python recommends `pyside6-deploy`, a Nuitka wrapper, over PyInstaller and others; from 6.12 the default mode is standalone, not onefile. Its page lists no signing or notarization option. The PyInstaller page still says "As of March 2021, Qt 6 is not supported yet", which the deployment index contradicts with "partial". ^[ambiguous]
- The same deploy page documents `[tool.pyside6.deploy]`. The PySide6 6.11.2 install read on 2026-10-18 has no such reader: settings come from `pysidedeploy.spec`, and `mode` defaults to `onefile`. Whether 6.12.0 implements the table was not checked. See [[projects/aenglisc-toolkit/skills/pyside6-deploy-on-6-11]]. ^[inferred]
- Signing options (`-hardened-runtime`, `-sign-for-notarization`) appear on the C++ `macdeployqt` page only.

## Limits

No PySide6 reference page was read for `QSettings`, `QStandardPaths`, `QLockFile`, `QPalette`, `QThreadPool`, `QUndoView` or `QUndoGroup`. No Qt blog post was found on `QTextEdit` many-block performance or on Widgets versus QML for document apps.

## Related

- [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-qt-idiom-plan]]
- [[skills/pyqt6-responsive-background-work]]
- [[skills/pyqt6-model-view-and-sql]]
- [[skills/pyqt6-actions-and-main-windows]]
- [[synthesis/Research: Qt and Translation Workbench Best Practice]]
- [[projects/aenglisc-toolkit/skills/pytest-qt-offscreen-macos]]
- [[projects/aenglisc-toolkit/skills/pyside6-deploy-on-6-11]]

## Sources

- Qt for Python documentation index and the Qt 6 pages listed in the front matter.
- [[_raw/_archived/2026-10-18-qt-offscreen-no-x11.md]]
- [[_raw/_archived/2026-10-18-pyside6-deploy-spec-only-config.md]]
