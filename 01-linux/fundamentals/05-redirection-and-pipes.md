# Redirection and Pipes

## Overview

By default, command output goes to the screen. Redirection sends it to files instead, and pipes pass it straight into another command. Together they turn single commands into workflows.

---

## Key Concepts

### Standard streams

Every command has three channels:

- **stdin (0)** - input, normally the keyboard
- **stdout (1)** - normal output
- **stderr (2)** - error messages

stdout and stderr both appear on screen, so they look the same until one is redirected.

---

## Operators

| Operator | Purpose |
|---|---|
| `>` | Write stdout to a file, overwriting it |
| `>>` | Append stdout to a file |
| `<` | Read input from a file |
| `2>` | Write stderr to a file |
| `&>` | Write both stdout and stderr to a file |
| `2>&1` | Send stderr to wherever stdout is going |
| `\|` | Pass one command's output into the next |

---

## Commands Practised

```bash
echo hello > notes.txt          # file now contains "hello"
echo hello >> notes.txt         # file now contains "hello" twice
ls missing 2> errors.txt        # error message saved to a file
ls missing /etc &> all.txt      # listing and error both saved
ls missing 2> /dev/null         # error discarded
head -n 10 file.txt | tail -n 5 # lines 6 to 10
```

`/dev/null` discards anything sent to it. It is useful for hiding noise, but it can also hide the errors I need.

---

> [!WARNING]
> `>` overwrites without asking. A mistyped file name on the right of `>` silently replaces that file's contents.

> [!IMPORTANT]
> `2>` only catches errors. If the command succeeds, its normal output still prints. I confused this once when the file I expected to be missing actually existed.

---

## Reflection

Seeing stdout and stderr split apart for the first time made the idea of streams click. `2>&1 | grep` has since become one of the most useful patterns I use for searching through build and log output.

⬅️ [Back to Fundamentals](./)
