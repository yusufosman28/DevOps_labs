# Wrong Remote URL

## Problem

My first push failed because the remote pointed at the wrong address. When I tried to add the remote again, Git refused:

```
error: remote origin already exists.
```

---

## Investigation

```bash
git remote -v
```

This showed the URL I had actually typed: `yusufosman128` instead of `yusufosman28` (my email has 1280 in it; my GitHub username does not), plus a stray full stop at the end.

---

## Cause

- The URL had a typo, so it pointed at an account and repository that did not exist.
- `git remote add` creates a new remote. `origin` already existed, so Git would not create it twice.

---

## Fix

```bash
git remote set-url origin https://github.com/yusufosman28/docker-learning.git
git remote -v      # confirmed the corrected URL
```

---

## What I Learned

- `git remote -v` shows exactly where a push will go
- `remote add` creates; `set-url` changes an existing remote
- Check usernames carefully: my email and my GitHub username are different

⬅️ [Back to Troubleshooting](./)
