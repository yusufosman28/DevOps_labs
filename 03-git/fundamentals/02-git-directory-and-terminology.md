# The .git Directory and Terminology

## Overview

A folder becomes a Git repository when it contains a hidden `.git` directory. That directory is the repository itself: all history, branches and configuration live inside it.

---

## Key Concepts

| Inside `.git/` | Holds |
|---|---|
| `objects/` | every commit, file and folder snapshot, stored by hash |
| `refs/` | branches and tags |
| `HEAD` | which branch or commit I am currently on |
| `index` | the staging area |
| `config` | settings for this repository, including remotes |

| Term | Meaning |
|---|---|
| **Repository** | a folder Git tracks |
| **Commit** | a snapshot plus author, date, message and a pointer to the previous commit |
| **Branch** | a pointer to a commit |
| **HEAD** | a pointer to where I currently am |
| **Remote / origin** | a copy of the repository hosted elsewhere; `origin` is the usual name |
| **Blob** | a file's content |
| **Tree** | a directory: links file names to blobs |
| **Tag** | a fixed name for a specific commit, often a release (`v1.0.0`) |

A repository contains commits; each commit points to a tree; trees point to blobs; branches and HEAD are pointers saying where I am.

---

## Commands Practised

```bash
git init          # creates the .git directory
ls -a             # .git is hidden, so -a is needed to see it
ls -la .git       # look inside
```

---

> [!WARNING]
> Deleting `.git` deletes the entire history. The files remain, but they are no longer tracked.

---

## Reflection

Realising that a branch is only a pointer explained why branching is instant: Git is not copying files, just writing a new pointer.

⬅️ [Back to Fundamentals](./)
