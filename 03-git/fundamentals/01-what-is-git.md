# What Git Is

## Overview

Git is a version control system: it records the history of a project so every change can be seen, compared and undone. Teams use it to work on the same code without overwriting each other, and DevOps pipelines use it as the trigger for builds and deployments.

---

## Key Concepts

- **A commit is a snapshot of the whole project**, not a list of changed lines. Unchanged files are not stored again; Git points to the existing copy, which keeps it fast.
- **Content-addressed:** Git identifies everything by a hash of its content. Identical content gets the same hash and is stored once.
- **Distributed:** every copy of a repository holds the full history, so Git works offline. There is no thin client depending on a central server.

| Git | GitHub |
|---|---|
| The version control tool | A platform that hosts Git repositories |
| Runs on my machine | Runs online |
| Works offline | Needs the internet |
| Tracks history | Adds collaboration: sharing, reviews, pull requests |

GitHub is one host among several; GitLab, Bitbucket and Azure DevOps do the same job with the same Git underneath.

---

## Commands Practised

```bash
git --version     # check Git is installed (mine: 2.53.0)
git config --global user.name "Yusuf Osman"
git config --global user.email "yusufosman1280@gmail.com"
git config --list # confirm the settings
```

---

> [!NOTE]
> The name and email set here are attached to every commit I make, so they need to be right before the first commit.

---

## Reflection

The snapshot idea changed how I think about Git. Once I stopped picturing tracked changes like a Word document, commands like `diff` and `log` made much more sense.

⬅️ [Back to Fundamentals](./)
