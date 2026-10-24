# Branching

## Overview

A branch lets me work on a change without touching the main project. If the work goes wrong, `main` is unaffected; if it goes well, it is merged back in.

---

## Key Concepts

- A branch is just a **pointer to a commit**, so creating one is instant and copies nothing.
- **`branch` makes, `switch` moves.** `git branch <name>` creates a branch and stays where I am; `git switch` moves onto one.
- `git switch` does one job. The older `git checkout` switches branches, restores files and moves to commits, which is why `switch` is clearer.
- Git blocks deleting a branch that has not been merged, to protect the work on it.

---

## Commands Practised

```bash
git branch                # list branches
git branch feature        # create, but stay on the current branch
git switch feature        # move onto it
git switch -c feature     # create and move in one step
git checkout -b feature   # older equivalent
git branch -d feature     # delete a merged branch
git branch -M main        # rename the current branch to main
```

---

> [!TIP]
> If a command contains `switch`, it moves me onto a branch. `git branch <name>` on its own never does.

---

## Reflection

"Branch makes, switch moves" stopped me committing to the wrong branch. It is the same reason I prefer `[[ ]]` over `[ ]` in Bash: the newer tool does one job clearly.

⬅️ [Back to Fundamentals](./)
