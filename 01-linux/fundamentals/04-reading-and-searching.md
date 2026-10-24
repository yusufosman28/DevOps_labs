# Reading and Searching

## Overview

A lot of DevOps work is reading: configuration files, logs and command output. Linux has small tools that each do one job well, from printing a whole file to showing only the lines that matter.

---

## Key Concepts

- `cat` shows everything, which is fine for short files
- `head` and `tail` show only the start or end
- `grep` filters output down to matching lines, like Ctrl+F for the terminal

On a log with thousands of lines, the recent errors are at the bottom, which is why `tail` is so useful.

---

## Commands Practised

```bash
cat config.txt                 # print the whole file
head -n 5 config.txt           # first 5 lines
tail -n 20 /var/log/syslog     # last 20 lines
grep error app.log             # lines containing "error"
grep -i error app.log          # ignore case: error, Error, ERROR
grep -i -E "error|failed" app.log   # match several patterns
```

`cat` can also combine files:

```bash
cat part1.txt part2.txt > combined.txt
```

### Filtering real output

I used `grep` to find the cause of a failed Docker build inside a long, noisy log:

```bash
docker build -t hello-flask-mysql . 2>&1 | grep -i -E "pkg-config|mysql_config|not found"
```

This returned `pkg-config: not found`, which pointed straight at the missing build tool.

---

> [!TIP]
> If `grep` returns nothing, the word may simply not be on any line. My first search for "error" only found a generic message; searching for the tool names found the real cause.

> [!NOTE]
> `grep word` with no file waits for input and looks frozen. `Ctrl+C` gets out.

---

## Reflection

Learning to filter output instead of scrolling through it changed how I debug. Knowing what to search for is the skill, and it improves with each real error.

⬅️ [Back to Fundamentals](./)
