# Bring a real terminal to Sublime Text

It is a cross platform terminal for Sublime Text which works on Windows, macOS and Linux.

<table>
    <tr>
        <th>Unix shell</th>
        <th>Cmd.exe</th>
    </tr>
    <tr>
        <td width="50%">
            <a href="https://user-images.githubusercontent.com/1690993/41784539-03534fdc-760e-11e8-845d-3d133a559df5.gif">
                <img src="https://user-images.githubusercontent.com/1690993/41784539-03534fdc-760e-11e8-845d-3d133a559df5.gif" width="100%">
            </a>
        </td>
        <td width="50%">
            <a href="https://user-images.githubusercontent.com/1690993/41786131-a625d870-7612-11e8-882d-f1574184faba.gif">
                <img src="https://user-images.githubusercontent.com/1690993/41786131-a625d870-7612-11e8-882d-f1574184faba.gif" width="100%">
            </a>
        </td>
    </tr>
    <tr>
        <th>Terminal in panel</th>
        <th></th>
    </tr>
    <tr>
        <td width="50%">
            <a href="https://user-images.githubusercontent.com/1690993/41784748-a7ed9d90-760e-11e8-8979-dd341933f1bb.gif">
                <img src="https://user-images.githubusercontent.com/1690993/41784748-a7ed9d90-760e-11e8-8979-dd341933f1bb.gif" width="100%">
            </a>
        </td>
        <td width="50%">
        </td>
    </tr>
</table>

This package is heavily inspired by [TerminalView](https://github.com/Wramberg/TerminalView). Compare with TerminalView, this has

- Windows support
- continuous history
- easily customizable themes
- unicode support
- 256 colors support
- better xterm support
- terminal panel

### Installation

This package is not yet available via Package Control default channel, you have to add the following repository manually.

- run `Package Control: Add Repository`
- paste

    ```
    https://raw.githubusercontent.com/randy3k/Terminus/master/package_control.json
    ```
    and hit enter

- then you could install it as usual - `Package Control: Install Package` and search for `Terminus`

### Getting started

- run `Terminus: Open Default Shell in View`


### User Key Bindings

There are various key bindings which you may found useful.

- run `Perferences: Terminus Key Bindings`

- toggle terminal panel
```js
{ "keys": ["alt+`"], "command": "toggle_terminus_panel" }
```

- close terminal in view or panel. It is particular useful for Window/Linux users who do not use `ctrl+w`; 
macOS users could use `super+w` to close any terminal.
```js
{ "keys": ["ctrl+w"], "command": "terminus_close" }
```

### Terminal Panel issue with DA UI

If your terminal panel has weired background color, try playing with the setting `panel_background_color` in `DA UI: Theme Settings`.

<img src="https://user-images.githubusercontent.com/1690993/41728204-31a9a2a2-7544-11e8-9fb6-a37b59da852a.png" width="50%" />

```js
{
    "panel_background_color": "$background_color"
}
```

### Note to other package developers

A terminal could be opened using the command `terminus_open` with
```py
window.run_command(
    "terminus_open", {
        config_name=None,  # the shell config name, the default config is "Default"
        cmd=None,          # the cmd to execuate if config_name is None
        cwd=None,          # the working directory
        env={},            # extra environmental variables
        title=None,        # title of the view
        panel_name=None,   # the name of the panel if terminal should be opened in panel
        tag=None           # a tag to identify the terminal
    }
)
```

Text can be sent to the terminal with
```py
window.run_command(
    "terminus_send_string", 
    {
        "string": "ls\n",
        "tag": None        # or the tag which is passed to "terminus_open"
    }
)
```
If `tag` is not provided, the text will be sent to the first terminal found in the current window.


### Acknowledgments

This package won't be possible without [pyte](https://github.com/selectel/pyte), [pywinpty](https://github.com/spyder-ide/pywinpty) and [ptyprocess](https://github.com/pexpect/ptyprocess).
