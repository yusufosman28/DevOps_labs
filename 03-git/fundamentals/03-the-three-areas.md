# The Three Areas

## Overview

Every change in Git moves through three areas before it becomes part of the history. Most beginner confusion comes from not knowing which area a file is in.

---

## Key Concepts

```
Working directory  --git add-->  Staging area  --git commit-->  Repository
```

- **Working directory:** the folder I edit in. Git can see changes here but has not recorded them.
- **Staging area (index):** the changes I have chosen for the next commit.
- **Repository:** the committed history stored in `.git`.

The staging area exists so I can choose exactly what goes into each commit, rather than committing everything at once.

---

## Commands Practised

```bash
git status            # which area each change is in
git add app.py        # working directory → staging
git status
git commit -m "add hello flask app"   # staging → repository
git status            # nothing to commit, working tree clean
```

In VS Code, `U` next to a file means untracked, `M` means modified, and `main*` in the status bar means there are uncommitted changes.

---

> [!IMPORTANT]
> Saving a file in VS Code does **not** mean Git has it. Saving writes to the working directory; Git only records it on `git add` and `git commit`.

> [!TIP]
> When Git confuses me, the question is: which area is this file in right now? `git status` answers it.

---

## Reflection

Running `git status` between every step made the three areas visible instead of abstract, and it is still the command I run most.

⬅️ [Back to Fundamentals](./)
