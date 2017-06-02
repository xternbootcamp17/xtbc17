+++
date = "2016-06-10T23:06:12-04:00"
next = "/tools/github-desktop"
prev = "/tools/code-extensions"
title = "VS Code Keybindings"
toc = true
weight = 1

+++

{{% h "vs-logo.svg" %}}
VS Code Keybindings
{{% /h %}}

It's worth your time to get to know the keyboard shortcuts for whatever editor you use. We've gone a step further and added some custom keybindings for some of the commands we use most.

## Custom Keybindings for VS Code

Open your Keyboard Shortcuts from the menu (<kbd>Code > Preferences > Keyboard Shortcuts</kbd>) or by using (what else?) the keyboard shortcut (<kbd>⌘</kbd>+<kbd>K</kbd>, <kbd>⌘</kbd>+<kbd>S</kbd>). From there, you can see all of the current keyboard shortcuts and customize them.

For serious customization, click the link to open _keybindings.js_. That opens two panes: the default keybindings, and your custom bindings. My keybindings appear below. I'll talk about a few of them.

{{< code js >}}
// Place your key bindings in this file to overwrite the defaults
[
  {
    "key": "alt+cmd+.",
    "command": "editor.emmet.action.matchingPair"
  },

  {
    "key": "shift+cmd+a",
    "command": "editor.emmet.action.wrapWithAbbreviation"
  },

  {
    "key": "cmd+'",
    "command": "esQuotes.transformBetweenSingleDoubleQuotes"
  },

  {
    "key": "ctrl+space",
    "command": "editor.emmet.action.expandAbbreviation",
    "when": "editorTextFocus && !editorHasMultipleSelections && !editorHasSelection && !editorReadonly"
  },

  {
      "key": "ctrl+shift+space",
      "command": "editor.emmet.action.splitJoinTag",
      "when": "editorTextFocus && !editorHasMultipleSelections && !editorHasSelection && !editorReadonly"
  },

  {
      "key": "ctrl+k ctrl+e",
      "command": "extension.embraceParenthesis",
      "when": "editorHasSelection && editorTextFocus"
  },

  {
      "key": "ctrl+k ctrl+[",
      "command": "extension.embraceSquareBrackets",
      "when": "editorHasSelection && editorTextFocus"
  },

  {
      "key": "ctrl+k ctrl+l",
      "command": "extension.embraceCurlyBrackets",
      "when": "editorHasSelection && editorTextFocus"
  },

  {
      "key": "ctrl+k ctrl+a",
      "command": "extension.embraceAngleBrackets",
      "when": "editorHasSelection && editorTextFocus"
  },

  {
      "key": "ctrl+k ctrl+'",
      "command": "extension.embraceSingleQuotes",
      "when": "editorHasSelection && editorTextFocus"
  },

  {
      "key": "ctrl+k ctrl+o",
      "command": "extension.embraceDoubleQuotes",
      "when": "editorHasSelection && editorTextFocus"
  }
]
{{< /code >}}

### Emmet

[Emmet](https://emmet.io/) is a wonderful tool for expanding CSS selector-like snippets into HTML elements. For example, type `.container>.row>.col-xs-12>p`, and Emmet will expand it into this:

{{< code html >}}
&lt;div class=&quot;container&quot;&gt;
  &lt;div class=&quot;row&quot;&gt;
    &lt;div class=&quot;col-xs-12&quot;&gt;
      &lt;p&gt;&lt;/p&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/div&gt;
{{< /code >}}

It will even put your cursor inside the `<p></p>` tags. And if you use it within JSX, it will use `className` instead of class, just as it should.

By default, IntelliSense will suggest Emmet expansion just like any other autocompletion. Sometimes that's fine, but other times it can be a real pain in the neck. Thus, I prefer to set a custom shortcut: <kbd>ctrl</kbd>+<kbd>space</kbd>.

When Emmet expands an abbreviation for a React component, it adds both a closing and opening tag.  Sometimes, we just want a single, self-closing tag.  In the keybindings listed in the previous section, we added one for `"editor.emmet.action.splitJoinTag"`.  This toggles between the open / closing tag and self-closing tag by pressing <kbd>ctrl</kbd>+<kbd>shift</kbd>+<kbd>space</kbd>

There's another really handy Emmet feature to which I've assigned a shortcut: _wrap with abbreviation_. It allows you to wrap a selection inside an HTML element identified by an Emmet abbreviation. Select the text you want to wrap and hit the shortcut. You'll be presented with a box to type the abbreviation into. Magic! I've assigned this command to <kbd>shift</kbd>+<kbd>⌘</kbd>+<kbd>A</kbd>. 

To make sure Emmet will work with JSX files suffixed with `.js`, add the following lines to your VSCode settings (<kbd>Code > Preferences > Settings</kbd>):

{{< code json >}}
"emmet.syntaxProfiles": {
    "javascript": "jsx"
}
{{< /code >}}

### ESQuotes

I mentioned the ECMAScript Quotes Transformer extension earlier. This begs for a keyboard shortcut to quickly switch between single and double quotes: <kbd>⌘</kbd>+<kbd>'</kbd>.

### Embrace

As mentioned on the previous page, the Embrace extension does not assign any keybindings by default, so I configured some. My shortcuts vary slightly from the recommended shortcuts on the extension's page (in particular, I prefer <kbd>ctrl</kbd>+<kbd>K</kbd>, <kbd>ctrl</kbd>+<kbd>[</kbd> for wrapping with square brackets).