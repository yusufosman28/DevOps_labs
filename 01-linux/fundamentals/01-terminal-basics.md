# Terminal Basics

## Overview

The terminal gives direct control over a Linux system through typed commands. In DevOps, most servers have no graphical interface at all, so moving around and reading information from the command line is the starting point for everything else.

---

## Key Concepts

### Command structure

Every command follows the same pattern, for example `ls -a /etc`:

- `ls` - the command
- `-a` - an option, which changes how the command behaves (starts with `-`)
- `/etc` - the argument, what the command acts on

Commands, options and file names are case-sensitive: `ls` works, `LS` does not.

### Options are not standard

The same letter can mean different things in different commands, and even different things in different case (`ls -r` reverses the order, `ls -R` lists recursively). The manual is the reliable way to check.

---

## Commands Practised

### `pwd` - Print working directory
Shows exactly where I am in the filesystem. The first thing I run when commands start failing unexpectedly.

### `ls` - List directory contents
```bash
ls          # files in the current directory
ls -a       # include hidden files (names starting with .)
ls -l       # long listing: permissions, owner, size, date
ls -la      # options can be combined
```

### `cd` - Change directory
```bash
cd projects     # into a folder
cd ..           # up one level
cd -            # back to the previous directory (not the parent)
cd ~            # home directory
```

### `man` - Manual pages
```bash
man ls          # full manual for ls; q to quit
```

### `history` and shortcuts
```bash
history         # numbered list of previous commands
!422            # rerun command number 422
sudo !!         # rerun the last command with sudo
```
`Tab` autocompletes names, `↑` recalls the last command, `Ctrl+C` cancels a command that hangs, and `Ctrl+L` clears the screen.

---

> [!WARNING]
> `cd -` goes to the **previous** directory, not the parent. `cd ..` is the parent.

---

## Reflection

Learning that every command follows the same structure made the terminal feel far less random. Checking `man` instead of guessing at options, and running `pwd` before assuming where I am, are the two habits that saved me the most time.

⬅️ [Back to Fundamentals](./)
