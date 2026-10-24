# Exit Codes and Error Handling

## Overview

Every command reports whether it succeeded through an exit code. By default, Bash ignores failures and carries on, which can turn a small problem into a wrong result much later. Error handling is about making failures visible.

---

## Key Concepts

- **`$?`** holds the exit code of the last command: `0` means success, anything else means failure.
- **`exit 1`** stops the whole script. **`return 1`** stops only the current function.

| Code | Meaning | Where I met it |
|---|---|---|
| `0` | success | `Exited (0)` on a finished container |
| `1` | general failure | a failed `pip install` in a Docker build |
| `127` | command not found | `pkg-config: not found` in a build |
| `137` | killed | a container force-stopped by `docker stop` |

| `set` option | Effect |
|---|---|
| `-e` | exit when any command fails |
| `-u` | error on an unset variable instead of treating it as empty |
| `-o pipefail` | a pipeline fails if any command in it fails |
| `-x` | print each command before it runs (debugging) |

---

## Commands Practised

```bash
ls
echo $?          # 0
nonexistentcmd
echo $?          # non-zero
```

Checking a dependency before using it:

```bash
command -v git > /dev/null 2>&1
if [ $? -ne 0 ]; then
    echo "git is not installed"
    exit 1
fi
```

Safety settings at the top of a script:

```bash
#!/bin/bash
set -euo pipefail
```

---

> [!WARNING]
> `$?` only holds the result of the **last** command, and every command overwrites it. Save it straight away with `exit_code=$?`.

> [!NOTE]
> The `set` flags are not the file tests. `set -e` means exit on error; `[ -e file ]` means "does the file exist".

---

## Reflection

A loud failure costs a few minutes; a silent one can cost hours because nobody is looking for it. That is why `set -euo pipefail` now goes at the top of my scripts.

⬅️ [Back to Fundamentals](./)
