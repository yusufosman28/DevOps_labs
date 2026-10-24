# Shell Basics

## Overview

The shell is the program that reads what I type and turns it into work the operating system can carry out. Understanding what sits between my keyboard and the machine explains a lot of errors, especially "command not found".

---

## Key Concepts

### How a command runs

**You → Shell → Kernel → Hardware**

- The **shell** (bash or zsh) interprets the command
- The **kernel** manages the machine's resources and does the real work
- The **hardware** is the physical machine

### Programs and binaries

Commands like `ls`, `cat` and `grep` are compiled programs (binaries) stored on disk, usually in `/bin` or `/usr/bin`.

### `PATH`

`PATH` is the list of folders the shell searches when I type a command. If a program's folder is not on that list, the shell cannot find it, even if the file exists.

---

## Commands Practised

```bash
which ls          # where the ls program is stored, e.g. /usr/bin/ls
echo $PATH        # the folders the shell searches, separated by :
echo $SHELL       # the shell I am using
cat /etc/shells   # shells available on the system
```

Typing the full path runs the same program without relying on `PATH`:

```bash
/usr/bin/ls
```

### Switching shells

```bash
zsh                     # start zsh for this session only
bash                    # back to bash
chsh -s $(which zsh)    # make zsh the default (applies to new sessions)
```

The prompt shows which shell and user I am working as: `$` for bash, `%` for zsh, `#` for root.

---

> [!NOTE]
> `$( )` runs a command first and uses its output. In `chsh -s $(which zsh)`, `which zsh` is replaced by the actual path to zsh.

---

## Reflection

Once I understood that the shell searches `PATH` to find programs, "command not found" stopped being a mystery. It usually means the program is not installed, or its folder is not on the list.

⬅️ [Back to Fundamentals](./)
