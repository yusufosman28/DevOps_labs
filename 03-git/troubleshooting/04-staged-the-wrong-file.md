# Staged the Wrong File

## Problem

Twice while working on `docker-learning`, I staged the wrong thing:

- After creating a new `Dockerfile`, I ran `git add app.py`, a file that had not changed.
- Later, I ran `git add "dockerfile"`: the wrong capitalisation, and `app.py` had also changed and needed staging too.

---

## Investigation

```bash
git status
```

This listed exactly which files had changed and which were untracked (`U` in VS Code), instead of the ones I assumed.

---

## Cause

I staged the files I expected to have changed instead of checking which files actually had. The file is called `Dockerfile` with a capital D, and Linux file names are case-sensitive.

---

## Fix

```bash
git add Dockerfile        # first time: the correct new file
git add .                 # second time: every changed file in the folder
git status                # confirmed what was staged
git commit -m "connect flask app to mysql and add build tools"
```

The second commit message covered both parts of the change, not just the database connection.

> [!TIP]
> `git status` before `git add` shows exactly what needs staging. `git status` after shows what will go into the commit.

---

## What I Learned

- Check what changed instead of assuming
- File names are case-sensitive: `Dockerfile`, not `dockerfile`
- Quotes are not needed around a file name with no spaces
- A commit message should describe the whole change

⬅️ [Back to Troubleshooting](./)
