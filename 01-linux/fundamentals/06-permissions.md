# Permissions

## Overview

Linux permissions control who can read, change or run each file. They are a core part of system security: correct permissions stop accidental changes and unauthorised access, while wrong ones break applications or expose sensitive files.

---

## Key Concepts

### Reading permissions

`ls -l` shows ten characters, for example `-rwxr-xr-x`:

- The first character is the type: `-` file, `d` directory
- Then three sets of three: **user** (owner), **group** and **others**
- `r` read, `w` write, `x` execute, `-` not granted

Linux checks in order (am I the owner? in the group? otherwise others) and stops at the first match.

### Octal notation

Each permission has a value: read = 4, write = 2, execute = 1. Adding them per set gives one digit each:

| Octal | Permissions | Typical use |
|---|---|---|
| `644` | `rw-r--r--` | Standard file |
| `755` | `rwxr-xr-x` | Script or program |
| `600` | `rw-------` | Private file |
| `400` | `r--------` | SSH private key |

### Least privilege

Only grant the access that is actually needed. It limits the damage from both mistakes and attacks.

---

## Commands Practised

```bash
ls -l script.sh                   # check current permissions
ls -ld projects                   # the folder's own permissions, not its contents
chmod u+x script.sh               # add execute for the owner
chmod g-w notes.txt               # remove write from the group
chmod o=r notes.txt               # set others to read only
chmod 750 script.sh               # set all permissions at once
sudo chown priya file.txt         # change owner
sudo chown priya:devops file.txt  # change owner and group
sudo chown -R priya:devops app/   # a folder and everything inside it
```

`+` and `-` adjust permissions. `=` and numbers replace them completely.

---

> [!WARNING]
> `chmod +x` with no letter gives execute to **everyone**. Use `u+x` to mean just the owner.

> [!IMPORTANT]
> Giving a file away does not remove my permissions; it moves me into **others**. If others has `---`, I am locked out. The question is always "which column am I in now?"

---

## Reflection

The idea that clicked was that permissions are about which category I fall into, not about me personally. Changing ownership changes the category, and that changes what I can do.

⬅️ [Back to Fundamentals](./)
