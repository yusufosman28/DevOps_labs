# Merging and History

## Overview

Merging brings work from one branch into another, usually back into `main`. Viewing history shows how branches split and joined, which matters when tracking down when and where a change came in.

---

## Key Concepts

- Merge **from the branch that receives the work**: switch to `main`, then merge the feature branch into it.
- **Fast-forward:** nothing new happened on `main`, so Git simply moves the `main` pointer forward. No new commit is created.
- **Merge commit:** both branches have new commits, so Git creates a commit joining them.
- **Conflict:** both branches changed the same lines of the same file. Git stops and I choose which version to keep.
- Plain `git log` only shows the current branch; `--all` shows every branch.

---

## Commands Practised

```bash
git switch main
git merge feature
```

Viewing history:

```bash
git log                             # full history of the current branch
git log --oneline                   # one line per commit
git log --oneline --graph --all     # every branch, drawn as a tree
```

---

> [!NOTE]
> Conflicts are normal and fixable. Git marks the conflicting lines in the file, and the merge completes once I edit, `add` and `commit`.

---

## Reflection

`git log --oneline --graph --all` made branching visible. Seeing the lines split and rejoin made fast-forward versus merge commit obvious in a way the explanation alone did not.

⬅️ [Back to Fundamentals](./)
