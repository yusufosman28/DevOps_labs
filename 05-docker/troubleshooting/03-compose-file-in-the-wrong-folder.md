# Compose File in the Wrong Folder

## Problem

My first `docker compose up` failed with two messages:

```
WARN ... the attribute `version` is obsolete, it will be ignored
failed to read dockerfile: open Dockerfile: no such file or directory
```

---

## Investigation

I first blamed the `version` line, because it appeared first and was highlighted. Reading both lines properly showed it was only a warning that would be ignored. The line that said **failed** was about the Dockerfile.

---

## Cause

I had created `docker-compose.yml` in `~/docker-learning`, but the Dockerfile is in `~/docker-learning/hello_flask`. In a compose file, `build: .` means "the folder this compose file is in", so Compose looked for a Dockerfile in the wrong place.

---

## Fix

```bash
mv docker-compose.yml hello_flask/
cd hello_flask
docker compose up
```

I also removed the obsolete `version` line. The stack built and started.

> [!TIP]
> A yellow `WARN` is information. The line containing **failed** or **error** is the one to fix.

---

## What I Learned

- `build: .` is relative to the compose file's location
- Compose must be run from the folder containing the compose file
- The most visible line is not always the cause

⬅️ [Back to Troubleshooting](./)
