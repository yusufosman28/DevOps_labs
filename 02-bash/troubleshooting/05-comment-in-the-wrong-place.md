# A Comment in the Wrong Place

## Problem

I was asked to comment out a line so it would stop running. I wrote:

```bash
echo # this line should not run
```

The script printed a blank line, and I assumed the line had been disabled.

---

## Investigation

A blank line is still output. Something had run.

---

## Cause

`#` disables everything **to its right**, not the whole line. `echo` came before the `#`, so it still ran, with nothing left to print.

---

## Fix

```bash
# echo "this line should not run"
```

With `#` at the very start, the whole line is ignored.

> [!NOTE]
> A blank line and no output look almost identical. Checking exactly what was printed caught the difference.

---

## What I Learned

- Where the `#` goes decides how much of the line survives
- "It looks like it worked" is not the same as checking that it did

⬅️ [Back to Troubleshooting](./)
