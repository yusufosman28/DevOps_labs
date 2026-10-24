# Vim Commands Saved as Text

## Problem

After trying to save and quit, my file contained the lines `Q`, `wq`, `q`, `q!` and `setnumber` as text. A small `[Command Line]` window had also opened and would not close.

---

## Investigation

The bottom-left of the screen showed `-- INSERT --`, which meant every key I pressed was being typed into the file.

---

## Cause

Two mistakes at once:

- I was in **insert mode**, where keys are text, not commands
- I typed commands **without a colon** (`wq` instead of `:wq`)

The `[Command Line]` window came from pressing `q:` instead of `:q`.

---

## Fix

```
Esc        return to command mode
:q!        quit and discard the damaged changes
```

Then I reopened the file and started again.

> [!TIP]
> `Esc` is always the first move when something goes wrong in Vim.

---

## What I Learned

- Check for `-- INSERT --` before typing a command
- Vim commands start with `:`
- Discarding with `:q!` is safer than trying to repair a file full of stray text

⬅️ [Back to Troubleshooting](./)
