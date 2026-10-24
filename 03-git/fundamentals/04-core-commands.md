# Core Commands

## Overview

A small set of commands covers almost all day-to-day Git work: starting a repository, recording changes, and checking what has changed.

---

## Key Concepts

| Command | Does |
|---|---|
| `git init` | turn a folder into a repository |
| `git status` | show what has changed and what is staged; changes nothing |
| `git add` | stage changes |
| `git commit -m` | record staged changes as a snapshot |
| `git diff` | show changes **not yet** staged |
| `git diff --staged` | show changes that **are** staged |
| `git log` | show commit history, newest first |

- `git add .` stages every changed file in the current folder. The `.` means "here", as in `cd .` and `docker build .`.
- Quotes are needed around a commit message with spaces, but not around a simple file name such as `Dockerfile`.

---

## Commands Practised

Order on a new project, with `status` between each step:

```bash
git init
git status
git add .
git status
git commit -m "initial commit"
git status
```

Checking changes:

```bash
git diff              # what I changed but have not staged
git add app.py
git diff              # empty: the change has moved to staging
git diff --staged     # shows it again
git log --oneline     # compact history
```

---

> [!WARNING]
> Staging a file and then running plain `git diff` shows nothing. The change is not lost; it has moved to the staging area. Use `git diff --staged`.

---

## Reflection

Treating `git status` as "opening my eyes" between every move meant I always knew what the next command would do before I ran it.

⬅️ [Back to Fundamentals](./)
