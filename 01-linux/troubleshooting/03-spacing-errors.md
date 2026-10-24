# Errors Caused by Spacing

## Problem

Three different commands failed:

```bash
chown sarah : admins file.txt
greeting = "hello"      # greeting: command not found
cd..                    # command not found
```

---

## Investigation

The errors looked unrelated, but comparing them showed the same pattern: each one was about where a space was, or was not.

---

## Cause

The shell uses spaces to decide where a command ends and each argument begins.

- `chown sarah : admins` - the extra spaces split `sarah:admins` into three separate arguments
- `greeting = "hello"` - the shell read `greeting` as a command name and went looking for it
- `cd..` - with no space, the shell looked for a command literally called `cd..`

> [!IMPORTANT]
> Spacing in shell commands is part of the syntax, not formatting.

---

## Fix

```bash
sudo chown sarah:admins file.txt
greeting="hello"
cd ..
```

---

## What I Learned

- Extra spaces split one value into several arguments
- A missing space joins two things into one
- The same rule later explained `COPY ..` vs `COPY . .` in a Dockerfile

⬅️ [Back to Troubleshooting](./)
