---
title: "MuseScore"
owner: "musescore"
source: "https://github.com/musescore/MuseScore"
website: "https://musescore.org/"
description: "MuseScore is an open source and free music notation software. For support, contribution, bug reports, visit MuseScore.org. Fork and make pull requests!"
stars: "15.3k"
language: "\"C++71.2%, CartoCSS17.8%, QML6.5%, C1.8%, CMake1%, Shell0.7%, Other1%\""
tags:
  - "qt"
  - "design"
created: 2026-10-17
---
## README

Music notation and composition software

[![License: GPL v3](https://camo.githubusercontent.com/1b0c7e4911720d0444c16a1ffd145a039f14a1a7305362ab51184f757a4dd6bc/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4c6963656e73652d47504c25323076332d626c75652e737667)](https://www.gnu.org/licenses/gpl-3.0.en.html) [![Coverage](https://camo.githubusercontent.com/20c434be1e839ac9ee0ff1fafd45f59938d68621c1f9f906b95a449ede4434c8/68747470733a2f2f73332e75732d656173742d312e616d617a6f6e6177732e636f6d2f657874656e73696f6e732e6d75736573636f72652e6f72672f746573742f636f64655f636f7665726167652f636f7665726167655f62616467652e7376673f)](https://github.com/musescore/MuseScore/actions/workflows/check_unit_tests.yml)

MuseScore Studio is an open source and free music notation software. For support, contribution, and bug reports visit MuseScore.org. Fork and make pull requests!

## Features

- WYSIWYG design, notes are entered on a "virtual notepaper"
- TrueType font(s) for printing & display allows for high quality scaling to all sizes
- Easy & fast note entry
- Many editing functions
- MusicXML import/export
- MIDI (SMF) import/export
- MEI import/export
- MuseData import
- MIDI input for note entry
- Integrated sequencer and software synthesizer to play the score
- Print or create PDF files

## More info

- [MuseScore Studio Homepage](https://musescore.org)
- [MuseScore Studio Git workflow instructions](https://musescore.org/en/developers-handbook/git-workflow)
- [How to compile MuseScore Studio?](https://github.com/musescore/MuseScore/wiki/Set-up-developer-environment)

## License

MuseScore Studio is licensed under GPL version 3.0. See [license file](https://github.com/musescore/MuseScore/blob/master/LICENSE.txt) in the same directory.

## Packages

See [Code Structure on Wiki](https://github.com/musescore/MuseScore/wiki/CodeStructure)

## Building

**Read the [Compilation section](https://github.com/musescore/MuseScore/wiki/Set-up-developer-environment) of the [MuseScore Wiki](https://github.com/musescore/MuseScore/wiki) for a complete build walkthrough and a list of dependencies.**

### Getting sources

If using git to download repo of entire code history, type:

```
git clone  --recurse-submodules https://github.com/musescore/MuseScore.git
cd MuseScore
```

Copy code to clipboard

(The `--recurse-submodules` ensures that the [`muse_framework`](https://github.com/musescore/muse_framework) git submodule is checked out into the `muse/` subdirectory.)

Otherwise, you can just download the latest source release tarball from the [Releases page](https://github.com/musescore/MuseScore/releases), and then from your download directory type:

```
tar xzf MuseScore-x.x.x.tar.gz
cd MuseScore-x.x.x
```

Copy code to clipboard

### Release Build

To compile MuseScore Studio for release, type:

```
cmake -P build.cmake -DCMAKE_BUILD_TYPE=Release
```

Copy code to clipboard

On MacOS, append `-G Ninja` in order to use the `ninja` build tool (which you may need to install), since this is required to compile Swift components.

If something goes wrong, append the word "clean" to the above command to delete the build subdirectory:

```
cmake -P build.cmake -DCMAKE_BUILD_TYPE=Release clean
```

Copy code to clipboard

Then try running the first command again.

### Running

To start MuseScore Studio, type:

```
cmake -P build.cmake -DCMAKE_BUILD_TYPE=Release run
```

Copy code to clipboard

Or run the compiled executable directly.

### Debug Build

A debug version can be built and run by replacing `-DCMAKE_BUILD_TYPE=Release` with `-DCMAKE_BUILD_TYPE=Debug` in the above commands.

If you omit the `-DCMAKE_BUILD_TYPE` option entirely then `RelWithDebInfo` is used by default, as it provides a useful compromise between Release and Debug.

### Testing

See the [Unit tests section](https://github.com/musescore/MuseScore/wiki/Unit-tests) of the [MuseScore Studio Wiki](https://github.com/musescore/MuseScore/wiki) for instructions on how to run the test suite.

### Code Formatting

Run `./hooks/install.sh` to install a pre-commit hook that will format your staged files. Requires that you install `uncrustify`.

If you have problems, please report them. To uninstall, run `./hooks/uninstall.sh`.

