# Size Test Gave Identical Results

## Problem

To compare image sizes, I made a second Dockerfile, `Dockerfile.full`, using the full `python:3.12` base image instead of slim. Both builds came out exactly the same size.

---

## Investigation

The VS Code tab for `Dockerfile.full` showed a `●` dot: unsaved. After saving and checking again, `docker images` still showed the **same image ID** as before.

---

## Cause

Two separate mistakes:

1. The first build used the file on disk, which still had the old `FROM` line because my change was not saved.
2. After saving, I had not rebuilt. Saving changes the recipe; only `docker build` produces a new image.

---

## Fix

```bash
docker build -f Dockerfile.full -t hello-flask-full .
docker images
```

The full image came out at 418 MB against 49.1 MB for slim: the slim image was about 88% smaller.

> [!TIP]
> An unchanged image ID in `docker images` means the image was not rebuilt.

---

## What I Learned

- Docker reads the file on disk, not what is open in the editor
- Saved is not built: changes only reach an image through a rebuild
- The image ID is a quick way to check whether a build actually produced something new

⬅️ [Back to Troubleshooting](./)
