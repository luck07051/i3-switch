## Description

Workspace switcher for i3wm that emulates XMonad/Qtile.


## Usage

`$ i3-switch-sp [-s] [-a] workspace [startup command]`

Depending on the state of target workspace different actions will apply:

| Tatget workspace statu    | Action                                       |
|---------------------------|----------------------------------------------|
| Not found                 | Spawn the workspace and exec startup command |
| Focused                   | Do nothing                                   |
| Not focused but visible   | Swap current and target workspace            |
| Not focused and unvisible | Move target workspace onto current monitor   |

With `-s` set, when target workspace focused, automatic exec `workspace back_and_forth`.

With `-a` set, when target workspace not focused but visible, just move the workspace onto current monitor, not swap then.

With `-s -a`, this will works like Scratchpad but workspace visible.


## Install

Just download `i3-switch-sp` and make it executable.

## Example

`sxhkd`
```
super + {1-9}
    i3-switch-sp {1-9}

super + w
    i3-switch-sp -s -a 10 "$TERMINAL --title vimwiki -e nvim $HOME/vimwiki/index.md"
```

`i3/config`
```
bindsym $mod+1 exec i3-switch-sp 1
...
```
