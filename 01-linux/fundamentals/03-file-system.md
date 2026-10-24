# File System

## Overview

Linux organises everything as a single tree that starts at `/` (root). Knowing where things live, and how to refer to them, is essential for navigating servers, editing configuration and reading logs.

---

## Key Concepts

### Key directories

| Path | Contains |
|---|---|
| `/` | The top of the filesystem |
| `/bin` | Everyday command programs |
| `/etc` | System configuration files |
| `/home` | Each user's personal folder |
| `/var` | Frequently changing data, including logs in `/var/log` |
| `/tmp` | Temporary files |
| `/root` | The root user's home folder |

`~` is shorthand for the current user's home directory.

### Absolute vs relative paths

- **Absolute** paths start with `/` and work from anywhere: `ls /etc`
- **Relative** paths start from the current directory: `ls etc`

The leading `/` is the whole difference.

### Hidden files

Files and folders whose names start with `.` are hidden from `ls`. `ls -a` shows them. Configuration files such as `.bashrc` are hidden this way.

---

## Commands Practised

```bash
touch notes.txt             # create an empty file (or update its timestamp)
mkdir -p projects/app/logs  # create nested folders in one step
cp notes.txt backup.txt     # copy a file
cp -r projects projects-bak # copy a folder and everything inside it
mv old.txt new.txt          # rename
mv notes.txt projects/      # move into an existing folder
rm notes.txt                # remove a file
rmdir empty-folder          # remove a folder only if it is empty
rm -r projects-bak          # remove a folder and everything inside it
```

Names with spaces need quotes or an escape:

```bash
mkdir "my project"
mkdir my\ project
```

---

> [!WARNING]
> `rmdir` refuses to delete a folder that is not empty, which acts as a safety net. `rm -r` has no such check, and `rm -rf /` would destroy the system.

> [!TIP]
> `-r` means **recursive**: do it all the way down. That is why `cp`, `rm` and `ls -R` need it for folders.

---

## Reflection

Most of my early navigation mistakes came from mixing up absolute and relative paths. Reading a path and asking "does this start from `/` or from where I am?" fixed most of them.

⬅️ [Back to Fundamentals](./)
