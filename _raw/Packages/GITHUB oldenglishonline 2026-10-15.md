---
title: "oldenglishonline"
owner: "vkkokko"
source: "https://github.com/vkkokko/oldenglishonline"
website: "https://oldinglish.info"
description: "An online educational resource for Old English."
stars: "31"
language: "\"EJS95.9%, CSS2.2%, JavaScript1.9%\""
tags:
  - "website"
  - "education"
  - "old_english"
created: 2026-10-15
---
## README

[![](https://camo.githubusercontent.com/16b63c986cb6632b5503cb87bf089bba8191ccb01294668f91b59d0dce40a043/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f7061636b6167652d6a736f6e2f762f766b6b6f6b6b6f2f6f6c64656e676c6973686f6e6c696e65)](https://camo.githubusercontent.com/16b63c986cb6632b5503cb87bf089bba8191ccb01294668f91b59d0dce40a043/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f7061636b6167652d6a736f6e2f762f766b6b6f6b6b6f2f6f6c64656e676c6973686f6e6c696e65) [![](https://camo.githubusercontent.com/2354b03d490edf08300baec8526feab0b90531f7e516d9ceb00e86d33353c464/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f636f6d6d69742d61637469766974792f772f766b6b6f6b6b6f2f6f6c64656e676c6973686f6e6c696e65)](https://camo.githubusercontent.com/2354b03d490edf08300baec8526feab0b90531f7e516d9ceb00e86d33353c464/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f636f6d6d69742d61637469766974792f772f766b6b6f6b6b6f2f6f6c64656e676c6973686f6e6c696e65)

# About

This is the file repository for Old English Online, an online learning platform for Old English. Uncompiled files are located in the *src* folder, while compiled files are located in the *docs* folder. Visit [oldenglish.info](https://oldenglish.info) to use the website.

#### Table Of Contents[Contributor's Guide](#Contributors-Guide)

- [How do I submit a good bug report?](#How-do-I-submit-a-good-bug-report)
- [How do I submit a good feature request?](#How-do-I-submit-a-good-feature-request)

[Developer's Guide](#Developers-Guide)

- [How to install Old English Online locally](#installing-and-running)

# Contributor's Guide

If you want to report a bug or suggest an enhancement, perform the following steps:

1. Create a Github account [here](https://github.com/) or just login if you already have one.
2. Navigate to the project repository on Github. It's [here](https://github.com/vkkokko/oldenglishonline).
3. Under the repository name, click **Issues**.
4. Click **New issue**.
5. Enter a title and description for your issue.
6. When you are finished, click **Submit** new issue

### How do I submit a good bug report?- **Use a clear and descriptive title** to identify what the issue is about.
- **Include all relevant information**. Mention the exact page you encountered the issue on, whether you were using a desktop or mobile, what browser you were accessing the site on, and how you triggered the issue. For example, "Using Google Chrome on my laptop, I clicked the 'Check' button under the quiz on Weak Verbs II and nothing happened".
- **Include screenshots**. This is especially important if you are reporting a graphical glitch or typo.

### How do I submit a good feature request?- **State what you want the feature to do**. For example, 'I would like it if you could review all the flashcards you've filled out in a session so you can see which ones you got right and which you got wrong'.
- **State where you would like the feature to go**. For example, 'I'd like there to be a button I could click on the flashcard modal which would bring up this information'.
- **State who you think the feature would benefit**. For example, is it aimed at first time learners or postgraduate scholars?

# Developer's Guide

## Installing and RunningTo run Old English Online locally on your machine so that you can contribute content or develop a new feature, you must perform the following steps:

1. Create a Github account [here](https://github.com/) or just login if you already have one.
2. Download a git client, you can get the free GitKraken [here](https://www.gitkraken.com/).
3. Navigate to the project repository on Github. It's [here](https://github.com/vkkokko/oldenglishonline).
4. Click the **Clone or download** button and copy the URL.
5. In GitKraken, choose **Clone Repo**, choose **From URL** and paste the URL you copied from Github. This copies the repository to your machine. Take a note of where you save it as you will need to know the path to the project in step 9.
6. Download an development environment. We recommend Visual Studio Code which you can download [here](https://code.visualstudio.com/).
7. Install the most recent version of Node.js. You can download it [here](https://nodejs.org/en/download/).
8. Open Visual Studio Code.
9. In Visual Studio Code, click **View** then **Terminal** to open the terminal.
10. The folder you are in should be on the last line in the terminal. Check this path to make sure you're in the root folder of the project. If you are not, you can change which directory you're in by typing `cd C:\whatever_your_filepath_is`. My root folder is C:\\Users\\Victoria\\Desktop\\OldEnglishOnline so I would type `cd C:\Users\Victoria\Desktop\OldEnglishOnline`.
11. Once you are in the root folder, type `npm install` and press **Enter**. Everything you need is installed automatically. This may take 2-3 minutes.
12. When it is finished, type `npm run start`. This builds the project, starts the watch tasks that wait for file changes, and opens the project in your default browser. **Note:** Sometimes your browser is a little too fast to load the page and will instead load a white page with a GET request. Just refresh the page and the correct content will load.
13. If the page does not load, navigate to *localhost:3000* in your browser.
14. Once the above steps are complete, you can make edits to the templates, scripts and styles in the `/src/` folder, and the project will automatically refresh in the browser to show your changes once they are saved.
15. Once you have made all your changes, save the file.
16. Commit your changes in GitKraken by selecting **Stage all changes**.
17. Push your work back up to your fork. If you're using GitKraken, you just need to click the **Push** button.
18. Submit a Pull Request so that we can review your changes.
19. An Administrator will then review and approve your changes.

# License- Content [licensed](/vkkokko/oldenglishonline/blob/master/LICENSE.md) under Creative Commons: [![License: CC BY-SA 3.0](https://camo.githubusercontent.com/86aec132bee602f6e82d3b428d63285458a21d7d927cabf38bc627a547bf3efe/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4c6963656e73652d434325323042592d2d5341253230332e302d6c69676874677265792e737667)](https://creativecommons.org/licenses/by-sa/3.0/)
- Code [licensed](/vkkokko/oldenglishonline/blob/master/LICENSE.md) under MIT: [![License: MIT](https://camo.githubusercontent.com/fdf2982b9f5d7489dcf44570e714e3a15fce6253e0cc6b5aa61a075aac2ff71b/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4c6963656e73652d4d49542d79656c6c6f772e737667)](https://opensource.org/licenses/MIT)

