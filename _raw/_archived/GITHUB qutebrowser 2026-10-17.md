---
title: "qutebrowser"
owner: "qutebrowser"
source: "https://github.com/qutebrowser/qutebrowser"
website: "https://www.qutebrowser.org/"
description: "A keyboard-driven, vim-like browser based on Python and Qt."
stars: "11.7k"
language: "\"Python75%, JavaScript14.1%, Gherkin6.8%, HTML2.4%, Shell0.9%, NSIS0.7%, Other0.1%\""
tags:
  - "qt"
  - "design"
created: 2026-10-17
---
## README

[![qutebrowser logo](/qutebrowser/qutebrowser/raw/main/qutebrowser/icons/qutebrowser-64x64.png)](/qutebrowser/qutebrowser/blob/main/qutebrowser/icons/qutebrowser-64x64.png) **A keyboard-driven, vim-like browser based on Python and Qt.**

[![Build Status](https://github.com/qutebrowser/qutebrowser/workflows/CI/badge.svg)](https://github.com/qutebrowser/qutebrowser/actions?query=workflow%3ACI) [![coverage badge](https://camo.githubusercontent.com/b11f8a97f248e6b1087305b91269a88286bc39a3f9c0bf8b18e88b97c346130b/68747470733a2f2f636f6465636f762e696f2f6769746875622f7175746562726f777365722f7175746562726f777365722f636f7665726167652e7376673f6272616e63683d6d61696e)](https://codecov.io/github/qutebrowser/qutebrowser?branch=main)

[website](https://www.qutebrowser.org) | [blog](https://blog.qutebrowser.org) | [FAQ](https://github.com/qutebrowser/qutebrowser/blob/main/doc/faq.asciidoc) | [contributing](https://www.qutebrowser.org/doc/contributing.html) | [releases](https://github.com/qutebrowser/qutebrowser/releases) | [installing](https://github.com/qutebrowser/qutebrowser/blob/main/doc/install.asciidoc)

qutebrowser is a keyboard-focused browser with a minimal GUI. It’s based on Python and Qt and free software, licensed under the GPL.

It was inspired by other browsers/addons like dwb and Vimperator/Pentadactyl.

**qutebrowser’s primary maintainer, The-Compiler, is currently working part-time on qutebrowser, funded by donations.** To sustain this for a long time, your help is needed! See the [GitHub Sponsors page](https://github.com/sponsors/The-Compiler/) or [alternative donation methods](https://github.com/qutebrowser/qutebrowser/blob/main/README.asciidoc#donating) for more information. Depending on your sign-up date and how long you keep a certain level, you can get qutebrowser t-shirts, stickers and more!

## Screenshots[![screenshot 1](/qutebrowser/qutebrowser/raw/main/doc/img/main.png)](/qutebrowser/qutebrowser/blob/main/doc/img/main.png) [![screenshot 2](/qutebrowser/qutebrowser/raw/main/doc/img/downloads.png)](/qutebrowser/qutebrowser/blob/main/doc/img/downloads.png) [![screenshot 3](/qutebrowser/qutebrowser/raw/main/doc/img/completion.png)](/qutebrowser/qutebrowser/blob/main/doc/img/completion.png) [![screenshot 4](/qutebrowser/qutebrowser/raw/main/doc/img/hints.png)](/qutebrowser/qutebrowser/blob/main/doc/img/hints.png)

## DownloadsSee the [GitHub releases page](https://github.com/qutebrowser/qutebrowser/releases) for available downloads and the [INSTALL](/qutebrowser/qutebrowser/blob/main/doc/install.asciidoc) file for detailed instructions on how to get qutebrowser running on various platforms.

## Documentation and getting helpPlease see the [help page](/qutebrowser/qutebrowser/blob/main/doc/help/index.asciidoc) for available documentation pages and support channels.

## Contributions / BugsYou want to contribute to qutebrowser? Awesome! Please read [the contribution guidelines](/qutebrowser/qutebrowser/blob/main/doc/contributing.asciidoc) for details and useful hints.

If you found a bug or have a feature request, you can report it in several ways:

- Use the built-in `:report` command or the automatic crash dialog.
- Open an issue in the Github issue tracker.
- Write a mail to the [mailinglist](https://listi.jpberlin.de/mailman/listinfo/qutebrowser) at [qutebrowser@lists.qutebrowser.org](mailto:qutebrowser@lists.qutebrowser.org).

Please report security bugs to [security@qutebrowser.org](mailto:security@qutebrowser.org) (or if GPG encryption is desired, contact [me@the-compiler.org](mailto:me@the-compiler.org) with GPG ID [0x916EB0C8FD55A072](https://www.the-compiler.org/pubkey.asc)).

Alternatively, [report a vulnerability](https://github.com/qutebrowser/qutebrowser/security/advisories/new) via GitHub’s [private reporting feature](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing/privately-reporting-a-security-vulnerability).

## RequirementsThe following software and libraries are required to run qutebrowser:

- [Python](https://www.python.org/) 3.10 or newer
- [Qt](https://www.qt.io/), either 6.2.0 or newer, or 5.15.0 or newer, with the following modules:
	- QtCore / qtbase
	- QtQuick (part of qtbase or qtdeclarative in some distributions)
	- QtSQL (part of qtbase in some distributions)
	- QtDBus (part of qtbase in some distributions; note that a connection to DBus at runtime is optional)
	- QtOpenGL
	- QtWebEngine (if using Qt 5, 5.15.2 or newer), or
	- alternatively QtWebKit (5.212) - **This is not recommended** due to known security issues in QtWebKit, you most likely want to use qutebrowser with the default QtWebEngine backend (based on Chromium) instead. Quoting the [QtWebKit releases page](https://github.com/qtwebkit/qtwebkit/releases): *\[The latest QtWebKit\] release is based on \[an\] old WebKit revision with known unpatched vulnerabilities. Please use it carefully and avoid visiting untrusted websites and using it for transmission of sensitive data.*
- [PyQt](https://www.riverbankcomputing.com/software/pyqt/intro) 6.2.2 or newer (Qt 6) or 5.15.0 or newer (Qt 5)
- [jinja2](https://palletsprojects.com/p/jinja/)
- [PyYAML](https://github.com/yaml/pyyaml)

On macOS, the following libraries are also required:

- [pyobjc-core and pyobjc-framework-Cocoa](https://pyobjc.readthedocs.io/en/latest/)

The following libraries are optional:

- [adblock](https://pypi.org/project/adblock/) (for improved adblocking using ABP syntax)
- [pygments](https://pygments.org/) for syntax highlighting with `:view-source` on QtWebKit, or when using `:view-source --pygments` with the (default) QtWebEngine backend.
- On Windows, [colorama](https://pypi.python.org/pypi/colorama/) for colored log output.
- [asciidoc](https://asciidoc.org/) to generate the documentation for the `:help` command, when using the git repository (rather than a release).

See [the documentation](/qutebrowser/qutebrowser/blob/main/doc/install.asciidoc) for directions on how to install qutebrowser and its dependencies.

## Donating**qutebrowser’s primary maintainer, The-Compiler, is currently working part-time on qutebrowser, funded by donations.** To sustain this for a long time, your help is needed! See the [GitHub Sponsors page](https://github.com/sponsors/The-Compiler/) for more information. Depending on your sign-up date and how long you keep a certain level, you can get qutebrowser t-shirts, stickers and more!

GitHub Sponsors allows for one-time donations (using the buttons next to "Select a tier") as well as custom amounts. **For currencies other than Euro or Swiss Francs, this is the preferred donation method.** GitHub uses [Stripe](https://stripe.com/) to accept payment via credit cards without any fees. Billing via PayPal is available as well, with less fees than a direct PayPal transaction.

Alternatively, the following donation methods are available — note that eligibility for swag (shirts/stickers/etc.) is handled on a case-by-case basis for those, please [get in touch](mailto:mail@qutebrowser.org) for details.

- [Liberapay](https://liberapay.com/The-Compiler), which can handle payments via Credit Card, SEPA bank transfers, or Paypal. Payment fees are paid by me, but they are [relatively low](https://liberapay.com/about/faq#fees).
- SEPA bank transfer inside Europe (**no fees**):
	- Account holder: Freya Bruhin
	- Country: Switzerland
	- IBAN (EUR): CH13 0900 0000 9160 4094 6
	- IBAN (other): CH80 0900 0000 8711 8587 3
	- Bank: PostFinance AG, Mingerstrasse 20, 3030 Bern, Switzerland (BIC: POFICHBEXXX)
	- If you need any other information: Contact me at [mail@qutebrowser.org](mailto:mail@qutebrowser.org).
	- If possible, **please consider yearly or semi-yearly donations**, because of the additional overhead from many individual transactions for bookkeeping/tax purposes.
- PayPal: [CHF](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=me%40the-compiler.org&item_name=qutebrowser&currency_code=CHF&source=url), [EUR](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=me%40the-compiler.org&item_name=qutebrowser&currency_code=EUR&source=url), [USD](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=me%40the-compiler.org&item_name=qutebrowser&currency_code=USD&source=url). **Note: Fees can be very high (around 5-40%, depending on the donated amounts)** - consider using GitHub Sponsors (credit card), Liberapay (credit cards, PayPal, or bank transfer) or SEPA bank transfers instead.
- Cryptocurrencies:
	- Bitcoin: bc1q3ptyw8hxrcfz6ucfgmglphfvhqpy8xr6k25p00
	- Bitcoin Cash: 1BnxUbnJ5MrEPeh5nuUMx83tbiRAvqJV3N
	- Ethereum: 0x10c2425856F7a8799EBCaac4943026803b1089c6
	- Litecoin: MDt3YQciuCh6QyFmr8TiWNxB94PVzbnPm2
	- Others: Please [get in touch](mailto:mail@qutebrowser.org), I’d happily set up anything [supported by Ledger Live](https://www.ledger.com/supported-crypto-assets)

## Authorsqutebrowser’s primary author is Freya Bruhin (The Compiler), but qutebrowser wouldn’t be what it is without the help of [hundreds of contributors](https://github.com/qutebrowser/qutebrowser/graphs/contributors)!

Additionally, the following people have contributed graphics:

- Jad/[yelo](https://yelostudio.com) (new icon)
- WOFall (original icon)
- regines (key binding cheatsheet)

Also, thanks to everyone who contributed to one of qutebrowser’s [crowdfunding campaigns](/qutebrowser/qutebrowser/blob/main/doc/backers.asciidoc)!

## Similar projectsVarious projects with a similar goal like qutebrowser exist. Many of them were inspirations for qutebrowser in some way, thanks for that!

### Active- [vimb](https://fanglingsu.github.io/vimb/) (C, GTK+ with WebKit2)
- [luakit](https://luakit.github.io/) (C/Lua, GTK+ with WebKit2)
- [Nyxt browser](https://nyxt.atlas.engineer/) (formerly "Next browser", Lisp, Emacs-like but also offers Vim bindings, QtWebEngine or GTK+/WebKit2 - note there was a [critical remote code execution in 2019](https://jgkamat.gitlab.io/blog/next-rce.html) which was handled quite badly)
- [Vieb](https://vieb.dev/) (JavaScript, Electron)
- [surf](https://surf.suckless.org/) (C, GTK+ with WebKit1/WebKit2)
- [wyeb](https://github.com/jun7/wyeb) (C, GTK+ with WebKit2)
- Chrome/Chromium addons: [Vimium](https://vimium.github.io/)
- Firefox addons (based on WebExtensions): [Tridactyl](https://tridactyl.xyz/), [Vimium-FF](https://addons.mozilla.org/en-GB/firefox/addon/vimium-ff/)
- Addons for Firefox and Chrome: [Surfingkeys](https://github.com/brookhong/Surfingkeys) ([somewhat sketchy](https://github.com/brookhong/Surfingkeys/issues/1796)…​), [Link Hints](https://lydell.github.io/LinkHints/) (hinting only), [Vimmatic](https://github.com/ueokande/vimmatic)

### Inactive- [dwb](https://bitbucket.org/portix/dwb) (C, GTK+ with WebKit1, [unmaintained](https://bitbucket.org/portix/dwb/pull-requests/22/several-cleanups-to-increase-portability/diff) - main inspiration for qutebrowser)
- [webmacs](https://github.com/parkouss/webmacs/) (Python, Emacs-like with QtWebEngine, [unmaintained](https://github.com/parkouss/webmacs/issues/137))
- [vimprobable](https://sourceforge.net/p/vimprobable/wiki/Home/) (C, GTK+ with WebKit1)
- [jumanji](https://pwmt.org/projects/jumanji/) (C, GTK+ with WebKit1)
- [conkeror](http://conkeror.org/) (Javascript, Emacs-like, XULRunner/Gecko)
- [uzbl](https://www.uzbl.org/) (C, GTK+ with WebKit1/WebKit2)
- [xombrero](https://github.com/conformal/xombrero) (C, GTK+ with WebKit1)
- [Cream Browser](https://github.com/linkdd/cream-browser) (C, GTK+ with WebKit1)
- Firefox addons (not based on WebExtensions or no recent activity): [Vimperator](http://www.vimperator.org/), [Pentadactyl](http://bug.5digits.org/pentadactyl/index), [VimFx](https://github.com/akhodakivskiy/VimFx) (seems to offer a [hack](https://gir.st/blog/legacyfox.htm) to run on modern Firefox releases), [QuantumVim](https://github.com/shinglyu/QuantumVim), [Vim Vixen](https://github.com/ueokande/vim-vixen), [VVimpulation](https://github.com/amedama41/vvimpulation), [Krabby](https://krabby.netlify.app/)
- Chrome/Chromium addons: [ViChrome](https://github.com/k2nr/ViChrome/), [Vrome](https://github.com/jinzhu/vrome), [Saka Key](https://github.com/lusakasa/saka-key) ([unmaintained](https://github.com/lusakasa/saka-key/issues/171)), [cVim](https://github.com/1995eaton/chromium-vim), [vb4c](https://github.com/dcchambers/vb4c) (fork of cVim, [unmaintained](https://github.com/dcchambers/vb4c/issues/23#issuecomment-810694017)), [GleeBox](https://glee.github.io/)
- Addons for Safari: [Vimari](https://televator.net/vimari/)

## LicenseThis program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program. If not, see [https://www.gnu.org/licenses/gpl-3.0.txt](https://www.gnu.org/licenses/gpl-3.0.txt).

## pdf.jsqutebrowser optionally uses [pdf.js](https://github.com/mozilla/pdf.js/) to display PDF files in the browser. Windows releases come with a bundled pdf.js.

pdf.js is distributed under the terms of the Apache License. You can find a copy of the license in `qutebrowser/3rdparty/pdfjs/LICENSE` (in the Windows release or after running `scripts/dev/update_3rdparty.py`), or online [here](https://www.apache.org/licenses/LICENSE-2.0.html).

