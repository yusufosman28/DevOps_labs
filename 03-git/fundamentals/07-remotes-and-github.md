# Remotes and GitHub

## Overview

A remote is a copy of the repository hosted somewhere else, such as GitHub. Pushing sends my commits there so they are backed up, shareable and available to CI/CD pipelines.

---

## Key Concepts

- **`origin`** is the conventional name for the main remote.
- **`-u`** (upstream) on the first push remembers the destination, so later pushes are just `git push`.
- **GitHub does not accept account passwords in the terminal.** Pushing needs a **personal access token** or signing in through an editor such as VS Code.
- **`git clone`** downloads a repository already connected to its remote, so no `init` or `remote add` is needed.
- **`git pull`** brings down changes made on GitHub, such as edits made in the browser.

---

## Commands Practised

How I pushed my first project, `docker-learning`:

```bash
git init
git add .
git commit -m "initial commit"
git branch -M main
git remote add origin https://github.com/yusufosman28/docker-learning.git
git remote -v                     # check the URL is correct
git push -u origin main
```

After that:

```bash
git push                          # upstream is remembered
git remote set-url origin <url>   # fix a wrong remote without removing it
git clone https://github.com/yusufosman28/DevOps_labs.git
git pull
```

---

> [!IMPORTANT]
> The repository must already exist on GitHub before pushing to it, or the push fails with "Repository not found".

> [!WARNING]
> A personal access token is a password. It should never be committed to a repository or shared, and mine is set to expire after 90 days.

---

## Reflection

My first push failed four different ways before it worked, and each error taught one piece of how remotes work. The write-ups are in [Troubleshooting](../troubleshooting).

⬅️ [Back to Fundamentals](./)
