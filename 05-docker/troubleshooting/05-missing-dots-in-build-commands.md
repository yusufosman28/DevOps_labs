# Missing Dots in Build Commands

## Problem

Two early mistakes in my first Dockerfile and build command:

```dockerfile
COPY ..
```

```bash
docker build -t hello-flask
```

```
ERROR: 'docker buildx build' requires 1 argument
```

---

## Investigation

Both lines were missing something to do with `.`, so I checked what Docker expects in each position.

---

## Cause

- `COPY` needs two paths: **from** and **to**. `..` with no space is a single path meaning "the folder above", so there was no destination.
- `docker build` needs to know where the Dockerfile and files are. The final `.` means "here", and without it there was no location at all.

---

## Fix

```dockerfile
COPY . .
```

```bash
docker build -t hello-flask .
```

> [!NOTE]
> The dot means "here" everywhere: `cd .`, `COPY . .`, `docker build .`, `code .`.

---

## What I Learned

- A space can change one argument into two, the same rule as in Bash
- `docker build` always needs a build location, usually `.`
- Reading the error literally ("requires 1 argument") pointed straight at the missing piece

⬅️ [Back to Troubleshooting](./)
