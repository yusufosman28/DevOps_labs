# `mysqlclient` Build Failed

## Problem

After adding `mysqlclient` to my Dockerfile so the Flask app could talk to MySQL, the build failed:

```
ERROR: failed to build: ... "pip install flask mysqlclient" did not complete successfully: exit code: 1
```

---

## Investigation

The output was long and squashed in the terminal, and scrolling did not show the reason. I filtered it with `grep`:

```bash
docker build -t hello-flask-mysql . 2>&1 | grep -i error
```

This only returned a generic message saying the error came from a subprocess. Searching for the tool names instead found the real line:

```bash
docker build -t hello-flask-mysql . 2>&1 | grep -i -E "pkg-config|mysql_config|not found"
```

```
/bin/sh: 1: pkg-config: not found
Command 'pkg-config --exists mysqlclient' returned non-zero exit status 127.
```

---

## Cause

`mysqlclient` is partly written in C, so pip has to compile it during the build. Compiling needs three things the slim Python image leaves out:

| Package | Why it is needed |
|---|---|
| `gcc` | the C compiler |
| `pkg-config` | finds where the MySQL files are; the one reported as missing |
| `default-libmysqlclient-dev` | the MySQL files `mysqlclient` builds against |

Exit status 127 means "command not found".

---

## Fix

Kept the slim image and added only the missing tools, above the pip line:

```dockerfile
RUN apt-get update && apt-get install -y gcc pkg-config default-libmysqlclient-dev
RUN pip install flask mysqlclient
```

- `apt-get update` first, because the slim image starts with an empty package list
- `-y` because nobody can answer "Do you want to continue?" during a build
- no `sudo`, because builds already run as root

The build succeeded.

> [!TIP]
> Switching to the full `python:3.12` image would also have worked, but it is 418 MB against 49.1 MB for slim. Adding three packages kept the image small.

---

## What I Learned

- `grep` only finds lines containing the word I search for; searching for tool names worked where "error" did not
- Slim images are small because they leave out build tools, and some Python packages need them
- Fix the specific gap instead of throwing away a good decision

⬅️ [Back to Troubleshooting](./)
