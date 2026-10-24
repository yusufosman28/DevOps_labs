# Vim Basics

## Overview

Vim is a text editor that runs inside the terminal, so it is available on almost every server. It works differently from a normal editor because it uses **modes**, which is what catches most beginners out.

---

## Key Concepts

| Mode | How to enter | Used for |
|---|---|---|
| Command (normal) | `Esc` (default on opening) | Moving, deleting, copying: keys act as commands |
| Insert | `i` | Typing text |
| Visual | `v` | Selecting text |

The bottom-left of the screen shows `-- INSERT --` in insert mode. If it is blank, keys are commands.

---

## Commands Practised

### Saving and quitting
```
:w      save
:q      quit (only if nothing is unsaved)
:wq     save and quit
:q!     quit and discard changes
```

### Moving and editing
```
h j k l     left, down, up, right
0 / $       start / end of line
G           last line of the file
dd          delete a line
yy / p      copy a line / paste
u / Ctrl+R  undo / redo
```

### Searching and display
```
/word         search forward; n for next, N for previous
:set number   show line numbers
:syntax on    colour highlighting
```

Editing a system file needs `sudo`, for example `sudo vim /etc/hosts`. Without it, the file opens read-only.

---

> [!IMPORTANT]
> Commands need a colon: `:wq`, not `wq`. Without it, in insert mode, the letters are typed into the file.

> [!TIP]
> When anything goes wrong, press `Esc` first. It always returns to command mode.

---

## Reflection

Vim only made sense once I stopped treating it like Notepad. Checking which mode I am in before typing removed nearly all of my mistakes.

⬅️ [Back to Fundamentals](./)
