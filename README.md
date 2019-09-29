Select all by current scope
===========================

Provides a `select_all_by_current_scope` command, which (as the name suggests) select everything matching the current scope (that is the scope of your first cursor).

The command accepts an optional argument `scope_must_match` containing a regex string, which filters the long scope string to get a single scope name.

**This plugin doesn't have any default keybindings.** You have to assign them yourself.

Example keybindings
-------------------

Selects everything matching current scope:
```json
[
  {
    "keys": ["ctrl+alt+shift+a"],
    "command": "select_all_by_current_scope"
  }
]
```
Selects everything matching the first piece of current scope, which contains the word `embedded`:
```json
[
  {
    "keys": ["ctrl+alt+shift+a"],
    "command": "select_all_by_current_scope",
    "args": { "scope_must_match": "embedded" }
  }
]
```

## Installation

### By Package Control

1. Download & Install `Sublime Text 3` (https://www.sublimetext.com/3)
1. Go to the menu `Tools -> Install Package Control`, then,
   wait few seconds until the `Package Control` installation finishes
1. Go to the menu `Preferences -> Package Control`
1. Type `Package Control Add Channel` on the opened quick panel and press <kbd>Enter</kbd>
1. Then, input the following address and press <kbd>Enter</kbd>
   ```
   https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json
   ```
1. Now, go again to the menu `Preferences -> Package Control`
1. This time type `Package Control Install Package` on the opened quick panel and press <kbd>Enter</kbd>
1. Then, search for `SelectAll` and press <kbd>Enter</kbd>

See also:
1. [ITE - Integrated Toolset Environment](https://github.com/evandrocoan/ITE)
1. [Package control docs](https://packagecontrol.io/docs/usage) for details.


Usecase
-------

Say you have a knitr/Sweave file with embedded R code. You might want to select all the R code. For that, I have the following keybinding:
```json
[
  {
    "keys": ["ctrl+alt+shift+a"],
    "command": "select_all_by_current_scope",
    "args": { "scope_must_match": "embedded" }
    "context": [
      { "key": "selector", "operator": "equal", "operand": "source.r.embedded.knitr" }
    ]
  }
]
```

How about all the javascript code from an HTML file? Bold text from a Markdown file? That's matched by default:
```json
[
  {
    "keys": ["ctrl+alt+shift+a"],
    "command": "select_all_by_current_scope"
  }
]
```
