# Environment Variables and PATH

## Overview

Environment variables are values the system sets for each session, such as the current user and home directory. Scripts read them like any other variable, which makes the same script work for different users and machines.

---

## Key Concepts

| Variable | Holds |
|---|---|
| `HOME` | home directory |
| `USER` | current username |
| `PWD` | current directory |
| `SHELL` | current shell |
| `PATH` | folders searched for commands |

- Changes made in the terminal disappear when the session ends.
- Adding them to the shell's config file (`~/.bashrc` for bash, `~/.zshrc` for zsh) loads them every time.
- `source` applies a config change to the current session without opening a new terminal.

---

## Commands Practised

```bash
echo "Hello, $USER. You are in $PWD"
```

Making a `PATH` change permanent:

```bash
mkdir ~/my-scripts
echo 'export PATH="$PATH:$HOME/my-scripts"' >> ~/.bashrc
source ~/.bashrc
```

`export PATH="$PATH:..."` keeps the existing folders and adds one at the end.

---

> [!WARNING]
> Use `>>` to append to the config file. `>` would overwrite the whole file.

---

## Reflection

Environment variables are also how values reach containers. The same idea appeared later as `-e MYSQL_ROOT_PASSWORD=...` in `docker run`.

⬅️ [Back to Fundamentals](./)
