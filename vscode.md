
# VS Code
- [VS Code](#vs-code)
    - [Extensions, User Settings, and the Command Pallete](#extensions-user-settings-and-the-command-pallete)
    - [General Setup](#general-setup)
    - [Github Integration](#github-integration)
    - [Setup for Latex](#setup-for-latex)
    - [Other Links and Material](#other-links-and-material)

:warning: As of September 2018, VS Code doesn't support Julia 1.0. 

## Extensions, User Settings, and the Command Pallete
**Command Palette:** 
Many features in VS Code are found through the Command Palette which can be accessed with `Ctrl+Shift+P`.  Throughout, these notes on OSX the `Ctrl` is the `⌘` button.  See https://code.visualstudio.com/docs/getstarted/userinterface for more on the VS Code UI.

**Extensions:** Go to the Extensions tab by clicking on the left side of VS Code, or `Ctrl+Shift+X`.  To find an extenion, type in part of the name into `Search Extensions in Marketplace`.  Alternatively, you can directly click "Install" button on the web links in the VS Code Marketplace

**User Settings:** To edit [Settings](https://code.visualstudio.com/docs/getstarted/settings) in VS Code, open up the user settings with `Ctrl+,` or opening up the command palette and starting to type `User Settings`.To find a particular settings, start typing in the name of the setting, extension, etc. Once you find it, you can select the `Edit` icon next to a particular setting to copy it to your local settings, and change it.

## General Setup
1. Install [VS Code](https://github.com/Microsoft/vscode)
2. *Optional*: Install [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one) 
    - Not required, but a good idea since [Markdown](markdown.md) is pervasive
    - For TOC compatability with github, go to the User Settings with `Ctrl+,` and then set `"markdown.extension.toc.githubCompatibility": true`
    - To have it show a preview immediately when you open one of the files, set`"markdown.extension.preview.autoShowPreviewToSide": true`
3. *Optional:* Install [Markdown PDF](https://marketplace.visualstudio.com/items?itemName=yzane.markdown-pdf) to export markdown   
3. *Optional:* It is convenient to globally change the word wrap, so choose `Ctrl+,` and then set `"editor.wordWrap": "on"`
4. *Optional:* It is convenient to make VSCode reload files automatically when loaded externally. To do this, so choose `Ctrl+,` and then set `"files.useExperimentalFileWatcher": true`
5. *Optional*: Install the [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) extension.

## Github Integration
- If you are working on a cloned repository, you can see changes in the `Source Control` tab, or with `Ctrl+Shift+G`.
- This will show you changes to the files, etc.  It will let you `Commit` with a message as well.
- The left hand side of the bottom bar on VS Code (or the Git repository in this tab) will let you Pull/Push/Sync
- A simple [Tutorial](https://www.youtube.com/watch?v=9cMWR-EGFuY) with more detail in [Using Version Control in VS Code](https://code.visualstudio.com/docs/editor/versioncontrol)

## Setup for Latex
1. If you just did the Julia setup, perhaps restart so you don't have the same windows cluttered.
2. *Optional*: While TeXLive already has it, if you have installed `MikTex` on Windows, you will need to manually setup SyncTex:
    - Download [kpathsea630.dll](https://www.tug.org/svn/texlive/trunk/Master/bin/win32/kpathsea630.dll?revision=46993&view=co)
    - Download [synctex.exe](https://www.tug.org/svn/texlive/trunk/Master/bin/win32/synctex.exe?revision=46993&view=co)
    - And place both of them in the miktex binaries folder, e.g. `C:\Program Files\MiKTeX 2.9\miktex\bin\x64`
3. Install the following packages in VS Code (clicking on them or using `Ctrl+Shift+X` to get the extensions)
  - [LaTex Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)
  - [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)
4. At this point, you should be able to open a test latex file.  Create a `test.tex` file with something like
```tex
\documentclass{article}
\begin{document}
TEST
\end{document}
```
4. Then go `Ctrl+Alt+B` to build the file then `Ctrl+Alt+V` to get the PDF preview.
5. If you make a change in the latex (e.g. change to `TESTS`) and save, if should automatically update the PDF.
7. *Optional*: Many latex packages require a compilation settings with shell access.
    - To do this, open up the user settings, `Ctrl+,` and start searching for `latex-workshop.latex.magic.args`
    - Copy it to the `USER SETTINGS` and modify, adding in a `"-shell-escape",` line.  It should look something like,
    ```JSON
    "latex-workshop.latex.magic.args": [
            "-synctex=1",
            "-interaction=nonstopmode",
            "-shell-escape",
            "-file-line-error",
            "%DOC%"
        ]
    ```
    - These settings are used whenever the magic comments are used in the latex file, e.g.
    ```tex
    % !TEX program = pdflatex
    % !BIB program = bibtex
    ```
8. *Optional:* For less irritating error messages, change to `"latex-workshop.message.error.show": false` and  `"latex-workshop.message.warning.show": false`

## Other Links and Material
- [Settings Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync) is an extension to maintain settings between different computers.  A little complicated to setup
- https://github.com/formulahendry/vscode-code-runner is another package... not sure it is useful for Julia or Python
- In the menu, go to `Help/Interactive Playground` to see features such as Multi-Cursor Editing, etc.
- Lots of places in VSCode, you're asked to describe things in a format called JSON (snippets, preferences, etc.) If this format is unfamiliar to you, [this site](https://code.tutsplus.com/tutorials/understanding-json--active-8817) provides a friendly tutorial. 
