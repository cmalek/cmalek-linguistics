---
title: "qtsass"
owner: "spyder-ide"
source: "https://github.com/spyder-ide/qtsass"
website:
description: "Compile SASS files to Qt stylesheets"
stars: "150"
language: "\"Python89.5%, Xonsh10.5%\""
tags:
  - "qt"
  - "design"
  - "stylesheet"
created: 2026-10-17
---
## README

[![License - MIT](https://camo.githubusercontent.com/63dbb80d9fd4ed48f99f3233ea338f7cfe1ea51ac6ca5e52674e971d8fc2604a/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f6c6963656e73652f7370796465722d6964652f7174736173732e737667)](/spyder-ide/qtsass/blob/master/LICENSE.txt) [![OpenCollective Backers](https://camo.githubusercontent.com/27512dadfce797c7be44856940e1152233d9bb6a9b37441f78fb28a1a4cb5a71/68747470733a2f2f6f70656e636f6c6c6563746976652e636f6d2f7370796465722f6261636b6572732f62616467652e7376673f636f6c6f723d626c7565)](#backers) [![Join the chat at https://gitter.im/spyder-ide/public](https://camo.githubusercontent.com/2a12b23f3c223721b601a3eec4aacfacaab5e6620295945e7c90a1b08e517299/68747470733a2f2f6261646765732e6769747465722e696d2f7370796465722d6964652f7370796465722e737667)](https://gitter.im/spyder-ide/public)  
[![Github build status](https://github.com/spyder-ide/qtsass/workflows/Tests/badge.svg)](https://github.com/spyder-ide/qtsass/actions) [![Codecov coverage](https://camo.githubusercontent.com/9e7b6474f8c52dd9e0e6bd6162184698777f510e14faaaccab75c34e1bc89d1c/68747470733a2f2f696d672e736869656c64732e696f2f636f6465636f762f632f6769746875622f7370796465722d6964652f7174736173732f6d61737465722e737667)](https://codecov.io/gh/spyder-ide/qtsass) [![Scrutinizer Code Quality](https://camo.githubusercontent.com/350f1caae613ec576fbd4ee80fc882209777c910ab58153077869a5471ebb9f7/68747470733a2f2f7363727574696e697a65722d63692e636f6d2f672f7370796465722d6964652f7174736173732f6261646765732f7175616c6974792d73636f72652e706e673f623d6d6173746572)](https://scrutinizer-ci.com/g/spyder-ide/qtsass/?branch=master)

*Copyright © 2015 Yann Lanthony*

*Copyright © 2017–2018 Spyder Project Contributors*

## Overview[SASS](http://sass-lang.com/) brings countless amazing features to CSS. Besides being used in web development, CSS is also the way to stylize Qt-based desktop applications. However, Qt's CSS has a few variations that prevent the direct use of SASS compiler.

The purpose of this tool is to fill the gap between SASS and Qt-CSS by handling those variations.

## Qt's CSS specificitiesThe goal of QtSASS is to be able to generate a Qt-CSS stylesheet based on a 100% valid SASS file. This is how it deals with Qt's specifics and how you should modify your CSS stylesheet to use QtSASS.

#### "!" in selectorsQt allows to define the style of a widget according to its states, like this:

```
QLineEdit:enabled {
...
}
```

Copy code to clipboard

However, a "not" state is problematic because it introduces an exclamation mark in the selector's name, which is not valid SASS/CSS:

```
QLineEdit:!editable {
...
}
```

Copy code to clipboard

QtSASS allows "!" in selectors' names; the SASS file is preprocessed and any occurence of `:!` is replaced by `:_qnot_` (for "Qt not"). However, using this feature prevents from having a 100% valid SASS file, so this support of `!` might change in the future. This can be replaced by the direct use of the `_qnot_` keyword in your SASS file:

```
QLineEdit:_qnot_editable { /* will generate QLineEdit:!editable { */
...
}
```

Copy code to clipboard

#### qlineargradientThe qlineargradient function also has a non-valid CSS syntax.

```
qlineargradient(x1: 0, y1: 0, x2: 0, y2: 1, stop: 0.1 blue, stop: 0.8 green)
```

Copy code to clipboard

To support qlineargradient QtSASS provides a preprocessor and a SASS implementation of the qlineargradient function. The above QSS syntax will be replaced with the following:

```
qlineargradient(0, 0, 0, 1, (0.1 blue, 0.8 green))
```

Copy code to clipboard

You may also use this syntax directly in your QtSASS.

```
qlineargradient(0, 0, 0, 1, (0.1 blue, 0.8 green))
# the stops parameter is a list, so you can also use variables:
$stops = 0.1 blue, 0.8 green
qlineargradient(0, 0, 0, 0, $stops)
```

Copy code to clipboard

#### qrgbaQt's rgba:

```
rgba(255, 128, 128, 50%)
```

Copy code to clipboard

is replaced by CSS rgba:

```
rgba(255, 128, 128, 0.5)
```

Copy code to clipboard

## Executable usageTo compile your SASS stylesheet to a Qt compliant CSS file:

```
# If -o is omitted, output will be printed to console
qtsass style.scss -o style.css
```

Copy code to clipboard

To use the watch mode and get your stylesheet auto recompiled on each file save:

```
# If -o is omitted, output will be print to console
qtsass style.scss -o style.css -w
```

Copy code to clipboard

To compile a directory containing SASS stylesheets to Qt compliant CSS files:

```
qtsass ./static/scss -o ./static/css
```

Copy code to clipboard

You can also use watch mode to watch the entire directory for changes.

```
qtsass ./static/scss -o ./static/css -w
```

Copy code to clipboard

Set the Environment Variable QTSASS\_DEBUG to 1 or pass the --debug flag to enable logging.

```
qtsass ./static/scss -o ./static/css --debug
```

Copy code to clipboard

## API methods### `compile(string, **kwargs)`Conform and Compile QtSASS source code to CSS.

This function conforms QtSASS to valid SCSS before passing it to sass.compile. Any keyword arguments you provide will be combined with qtsass's default keyword arguments and passed to sass.compile.

Examples:

```
>>> import qtsass
>>> qtsass.compile("QWidget {background: rgb(0, 0, 0);}")
QWidget {background:black;}
```

Copy code to clipboard

Arguments:

- string: QtSASS source code to conform and compile.
- kwargs: Keyword arguments to pass to sass.compile

Returns:

- Qt compliant CSS string

### `compile_filename(input_file, output_file=None, **kwargs)`:Compile and return a QtSASS file as Qt compliant CSS. Optionally save to a file.

Examples:

```
>>> import qtsass
>>> qtsass.compile_filename("dummy.scss", "dummy.css")
>>> css = qtsass.compile_filename("dummy.scss")
```

Copy code to clipboard

Arguments:

- input\_file: Path to QtSass file.
- output\_file: Path to write Qt compliant CSS.
- kwargs: Keyword arguments to pass to sass.compile

Returns:

- Qt compliant CSS string

### `compile_dirname(input_dir, output_dir, **kwargs)`:Compiles QtSASS files in a directory including subdirectories.

```
>>> import qtsass
>>> qtsass.compile_dirname("./scss", "./css")
```

Copy code to clipboard

Arguments:

- input\_dir: Path to directory containing QtSass files.
- output\_dir: Directory to write compiled Qt compliant CSS files to.
- kwargs: Keyword arguments to pass to sass.compile

### `enable_logging(level=None, handler=None)`:Enable logging for qtsass.

Sets the qtsass logger's level to: 1. the provided logging level 2. logging.DEBUG if the QTSASS\_DEBUG envvar is a True value 3. logging.WARNING

```
>>> import logging
>>> import qtsass
>>> handler = logging.StreamHandler()
>>> formatter = logging.Formatter('%(level)-8s: %(name)s> %(message)s')
>>> handler.setFormatter(formatter)
>>> qtsass.enable_logging(level=logging.DEBUG, handler=handler)
```

Copy code to clipboard

Arguments:

- level: Optional logging level
- handler: Optional handler to add

### `watch(source, destination, compiler=None, Watcher=None)`:Watches a source file or directory, compiling QtSass files when modified.

The compiler function defaults to compile\_filename when source is a file and compile\_dirname when source is a directory.

Arguments:

- source: Path to source QtSass file or directory.
- destination: Path to output css file or directory.
- compiler: Compile function (optional)
- Watcher: Defaults to qtsass.watchers.Watcher (optional)

Returns:

- qtsass.watchers.Watcher instance

## ContributingEveryone is welcome to contribute!

## SponsorsSpyder and its subprojects are funded thanks to the generous support of

[![Quansight](https://camo.githubusercontent.com/85b7e532f15802693c164fe6d8cb47ebd88cf4ea8ba4e84fa78e9fda1d558081/68747470733a2f2f7374617469632e7769787374617469632e636f6d2f6d656469612f3039356432635f32353038633536306538376434333665613030333537616263343034636631647e6d76322e706e672f76312f63726f702f785f302c795f392c775f3931352c685f3332392f66696c6c2f775f3338302c685f3132382c616c5f632c75736d5f302e36365f312e30305f302e30312f3039356432635f32353038633536306538376434333665613030333537616263343034636631647e6d76322e706e67)](https://www.quansight.com/)[![Numfocus](https://camo.githubusercontent.com/9e5cdb457cbb6224aee85719986f67427ab760ff8c3b4c6dd45672b0cd205c18/68747470733a2f2f69322e77702e636f6d2f6e756d666f6375732e6f72672f77702d636f6e74656e742f75706c6f6164732f323031372f30372f4e756d466f6375735f4c52472e706e673f6669743d3332302532433134382673736c3d31)](https://numfocus.org/)

and the donations we have received from our users around the world through [Open Collective](https://opencollective.com/spyder/):

[![Sponsors](https://camo.githubusercontent.com/67b3440f02ca09bbe3530c0252424f35327fc6ff991f4e9e82b0ea634de2a4e9/68747470733a2f2f6f70656e636f6c6c6563746976652e636f6d2f7370796465722f73706f6e736f72732e737667)](https://opencollective.com/spyder#support)

Please consider becoming a sponsor!

