+++
date = "2016-06-10T23:06:12-04:00"
next = "/tools/code-keybindings"
prev = "/tools"
title = "VS Code Extensions"
toc = true
weight = 1

+++

{{% h "vs-logo.svg" %}}
VS Code Extensions
{{% /h %}}

We use a number of settings, shortcuts, and extensions to make our lives easier when developing with Visual Studio Code. Here are some of our favorites extensions.

## Recommended Extensions for VS Code

To install an extension, launch VS Code Quick Open (<kbd>⌘</kbd>+<kbd>P</kbd>), paste the command, and press <kbd>enter</kbd>.


### [**vscode-icons**](https://marketplace.visualstudio.com/items?itemName=robertohuertasm.vscode-icons)

`ext install vscode-icons`

vscode-icons shows icons in the sidebar that correspond to the file type.

### [**Can I Use**](https://marketplace.visualstudio.com/items?itemName=akamud.vscode-caniuse)

`ext install vscode-caniuse`

Can I Use checks HTML/CSS/JS for browser compatibility, based on [caniuse.com](http://caniuse.com). The default keybinding is <kbd>ctrl</kbd>+<kbd>shift</kbd>+<kbd>i</kbd> on Windows/Linux and <kbd>ctrl</kbd>+<kbd>c</kbd> on Mac.

<img src="/images/caniuse.png" class='no-margin'>

### [**Color Highlight**](https://marketplace.visualstudio.com/items?itemName=naumovs.color-highlight)

`ext install color-highlight`

Color Highlights display web colors in your code _in that color_.

<img src="/images/color-highlight.png" class='no-margin'>

### [Debugger for Chrome](https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome)

`ext install debugger-for-chrome`

Debug in Chrome from inside VS Code. Pick a launch config from the dropdown on the Debug pane in Code, and press the play button or <kbd>F5</kbd> to start.

For React projects, create the file `.vscode/launch.json` in your project with the following configuration ([more info](https://medium.com/@auchenberg/live-edit-and-debug-your-react-apps-directly-from-vs-code-without-leaving-the-editor-3da489ed905f)):

{{< code json >}}
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Chrome",
      "type": "chrome",
      "request": "launch",
      "url": "http://localhost:3000",
      "webRoot": "${workspaceRoot}/src",
      "userDataDir": "${workspaceRoot}/.chrome",
      "sourceMapPathOverrides": {
          "webpack:///src/*": "${webRoot}/*"
      }
    }
  ]
}
{{< /code >}}

<img src="/images/debugger-react.gif" class='no-margin'>

### [ECMAScript Quotes Transformer](https://marketplace.visualstudio.com/items?itemName=vilicvane.es-quotes)

`ext install es-quotes`

Switches a string between single and double quotes, and between normal strings and ES6+ template strings.

<img src="/images/es-quotes.gif" class='no-margin'>

### [Embrace](https://marketplace.visualstudio.com/items?itemName=mycelo.embrace)

`ext install embrace`

Surround the selection with parentheses, brackets, quotes, etc. The extension does _not_ configure any keybindings for these commands by default.

### [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

`ext install vscode-eslint`

Check JavaScript for errors and style violations as you edit. Requires ESLint, which you can install with:

{{< term >}}
npm install eslint -g
{{< /term >}}

### [HTML Boilerplate](https://marketplace.visualstudio.com/items?itemName=sidthesloth.html5-boilerplate)

`ext install html5-boilerplate`

Adds a snippet for HTML 5 boilerplate.

<img src="/images/html-boilerplate.gif" class='no-margin'>

### [Path Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense)

`ext install path-intellisense`

Autocomplete filenames as you type. Very handy for module imports.

<img src="/images/path-intellisense.gif" class='no-margin'>

### [View In Browser](https://marketplace.visualstudio.com/items?itemName=qinjia.view-in-browser)

`ext install view-in-browser`

Opens an HTML page in the default browser. Bound to <kbd>⌘</kbd>+<kbd>F1</kbd> (Mac) or <kbd>ctrl</kbd>+<kbd>F1</kbd> by default.

{{% aside tip "Theme Info" %}}
Since I'm always asked, I use the following themes:

* Code: _Oceanic Next Italic_
* Atom: _Atom Dark_ UI theme; _Kobalt_ syntax theme (with some personal customizations)
{{% /aside %}}
