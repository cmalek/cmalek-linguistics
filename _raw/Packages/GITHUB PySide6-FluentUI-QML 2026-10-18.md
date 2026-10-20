---
title: "PySide6-FluentUI-QML"
owner: "zhuzichu520"
source: "https://github.com/zhuzichu520/PySide6-FluentUI-QML"
website:
description: "FluentUI for PySide6 and QML"
stars: "459"
language: "\"QML78.7%, Python21.3%\""
tags:
  - "qt"
  - "design"
  - "fluent"
created: 2026-10-18
---
## README

# PLEASE USE THE BRAND NEW [FluentUI Pro](https://github.com/zhuzichu520/FluentUI2) INSTEAD! [![](/zhuzichu520/PySide6-FluentUI-QML/raw/main/doc/preview/fluent_design.svg)](/zhuzichu520/PySide6-FluentUI-QML/blob/main/doc/preview/fluent_design.svg)

# QML FluentUIA fluent design component library for Qt QML， You need C++ [FluentUI](https://github.com/zhuzichu520/FluentUI)。

[![win-badge](https://github.com/zhuzichu520/FluentUI/workflows/Windows/badge.svg "Windows")](https://github.com/zhuzichu520/FluentUI/workflows/Windows/badge.svg) [![ubuntu-badge](https://github.com/zhuzichu520/FluentUI/workflows/Ubuntu/badge.svg "Ubuntu")](https://github.com/zhuzichu520/FluentUI/workflows/Ubuntu/badge.svg) [![macos-badge](https://github.com/zhuzichu520/FluentUI/workflows/MacOS/badge.svg "MacOS")](https://github.com/zhuzichu520/FluentUI/workflows/MacOS/badge.svg) [![release-badge](https://camo.githubusercontent.com/db93c035f033917aca7037220d071f844844ff5d1a47ae3e00c2f2519c3e24ff/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f72656c656173652f7a68757a696368753532302f466c75656e7455492e7376673f7374796c653d666c61742d737175617265 "Release status")](https://camo.githubusercontent.com/db93c035f033917aca7037220d071f844844ff5d1a47ae3e00c2f2519c3e24ff/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f72656c656173652f7a68757a696368753532302f466c75656e7455492e7376673f7374796c653d666c61742d737175617265) [![download-badge](https://camo.githubusercontent.com/0b0e25f95bd4997975380210558a3e43858f73b4fa9b83cb738f25d3e40c541b/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f646f776e6c6f6164732f7a68757a696368753532302f466c75656e7455492f746f74616c2e737667 "Download status")](https://camo.githubusercontent.com/0b0e25f95bd4997975380210558a3e43858f73b4fa9b83cb738f25d3e40c541b/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f646f776e6c6f6164732f7a68757a696368753532302f466c75656e7455492f746f74616c2e737667) [![download-latest](https://camo.githubusercontent.com/1c91630db76ab5eb86bef95f707d7912752da93dc4658bd1ccfcdf8e8add5c9b/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f646f776e6c6f6164732f7a68757a696368753532302f507953696465362d466c75656e7455492d514d4c2f6c61746573742f746f74616c2e737667 "latest status")](https://camo.githubusercontent.com/1c91630db76ab5eb86bef95f707d7912752da93dc4658bd1ccfcdf8e8add5c9b/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f646f776e6c6f6164732f7a68757a696368753532302f507953696465362d466c75656e7455492d514d4c2f6c61746573742f746f74616c2e737667)

English | [简体中文](/zhuzichu520/PySide6-FluentUI-QML/blob/main/README_zh_CN.md)

[![](/zhuzichu520/PySide6-FluentUI-QML/raw/main/doc/preview/demo_large.png)](/zhuzichu520/PySide6-FluentUI-QML/blob/main/doc/preview/demo_large.png)

## Requirements- Python 3.11

## ⚽ Get started- run `example` program.

```
git clone --recursive https://github.com/zhuzichu520/PySide6-FluentUI-QML.git
```

Copy code to clipboard

- Build

```
git clone --recursive https://github.com/zhuzichu520/PySide6-FluentUI-QML.git
cd PySide6-FluentUI-QML
python ./script-init-venv.py
python ./script-start.py
python ./script-build-nuitka.py
```

Copy code to clipboard

## 📑 Documentations(Work in progress...🚀)

## Supported components| Catalog | Detail | Notes / Demos |
| --- | --- | --- |
| FluApp | The initial entry of the program | Router supported(SPA) |
| FluWindow | Frameless Window | \*This only works on windows |
| FluAppBar | Title bar on top of the window | Drag, minimize, maximize and close are supported. |
| FluText | Common text |  |
| FluButton | Common button | [![btn](/zhuzichu520/PySide6-FluentUI-QML/raw/main/doc/preview/demo_standardbtn.png)](/zhuzichu520/PySide6-FluentUI-QML/blob/main/doc/preview/demo_standardbtn.png) |
| FluFilledButton | Filled button | [![filledbtn](/zhuzichu520/PySide6-FluentUI-QML/raw/main/doc/preview/demo_filledbtn.png)](/zhuzichu520/PySide6-FluentUI-QML/blob/main/doc/preview/demo_filledbtn.png) |
| FluTextButton | Text button | [![textbtn](/zhuzichu520/PySide6-FluentUI-QML/raw/main/doc/preview/demo_textbtn.png)](/zhuzichu520/PySide6-FluentUI-QML/blob/main/doc/preview/demo_textbtn.png) |
| FluToggleButton | Toggle buttons | [![togglebtn](/zhuzichu520/PySide6-FluentUI-QML/raw/main/doc/preview/demo_toggle_btn.png)](/zhuzichu520/PySide6-FluentUI-QML/blob/main/doc/preview/demo_toggle_btn.png) |
| FluIcon | Common icon | [![icons](/zhuzichu520/PySide6-FluentUI-QML/raw/main/doc/preview/demo_icon.png)](/zhuzichu520/PySide6-FluentUI-QML/blob/main/doc/preview/demo_icon.png) |
| FluRadioButton | radio button | [![radiobtn](/zhuzichu520/PySide6-FluentUI-QML/raw/main/doc/preview/demo_radiobtn.png)](/zhuzichu520/PySide6-FluentUI-QML/blob/main/doc/preview/demo_radiobtn.png) |
| FluTextBox | Single-line input box | [![textbox](/zhuzichu520/PySide6-FluentUI-QML/raw/main/doc/preview/demo_textbox.png)](/zhuzichu520/PySide6-FluentUI-QML/blob/main/doc/preview/demo_textbox.png) |
| FluMultiLineTextBox | Multi-lines input area | [![textarea](/zhuzichu520/PySide6-FluentUI-QML/raw/main/doc/preview/demo_multiline_textbox.png)](/zhuzichu520/PySide6-FluentUI-QML/blob/main/doc/preview/demo_multiline_textbox.png) |
| FluToggleSwitch | toggle switch | [![toggleswitch](/zhuzichu520/PySide6-FluentUI-QML/raw/main/doc/preview/demo_toggle_switch.png)](/zhuzichu520/PySide6-FluentUI-QML/blob/main/doc/preview/demo_toggle_switch.png) |

View more [`here`](/zhuzichu520/PySide6-FluentUI-QML/blob/main/doc/md/all_components.md)!

## Reference- [**FluentUI for qml**: C++ and QML.](https://github.com/zhuzichu520/FluentUI)
- [**Windows design**: Design guidelines and toolkits of Microsoft.](https://learn.microsoft.com/en-us/windows/apps/design/)
- [**Microsoft/WinUI-Gallery**: Microsoft's demo](https://github.com/microsoft/WinUI-Gallery)

## LicenseThis FluentUI library currently licensed under [MIT License](/zhuzichu520/PySide6-FluentUI-QML/blob/main/License)

## Star History[![Star History Chart](https://camo.githubusercontent.com/ba928a638ff16f7bb90cbac1f165db390b68564a98aaf14d5006f22c4afda75e/68747470733a2f2f6170692e737461722d686973746f72792e636f6d2f7376673f7265706f733d7a68757a696368753532302f507953696465362d466c75656e7455492d514d4c26747970653d44617465)](https://star-history.com/#zhuzichu520/PySide6-FluentUI-QML&Date)

## ⚡ Visitor count[![](https://camo.githubusercontent.com/8bef18862f15484893c3f6a2df1b656f0cba4fd39fc178317a69181e57ebe23b/68747470733a2f2f70726f66696c652d636f756e7465722e676c697463682e6d652f7a68757a696368753532302d507953696465362d466c75656e7455492d514d4c2f636f756e742e737667)](https://camo.githubusercontent.com/8bef18862f15484893c3f6a2df1b656f0cba4fd39fc178317a69181e57ebe23b/68747470733a2f2f70726f66696c652d636f756e7465722e676c697463682e6d652f7a68757a696368753532302d507953696465362d466c75656e7455492d514d4c2f636f756e742e737667)

