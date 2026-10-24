# A Syntax Error That Stayed Hidden

## Problem

My script contained a broken line, but it ran without any error:

```bash
if [ $age -gt 18 ]; then
    if [$grade -ge 80]; then     # broken: no spaces inside the brackets
        echo "Eligible"
    fi
fi
```

---

## Investigation

The broken line only came to light when I read through the code. Running the script had never triggered it, because the test value for `age` made the outer condition false.

---

## Cause

Bash only reports errors on lines it actually **executes**. The broken line sat inside a branch that never ran, so Bash never read it.

---

## Fix

```bash
if [ $grade -ge 80 ]; then
```

Then I tested with values that made **every** branch run.

> [!WARNING]
> A script passing once does not mean every branch is correct.

---

## What I Learned

- Untested branches can hide errors indefinitely
- Testing needs inputs that reach each path, not just the common one

⬅️ [Back to Troubleshooting](./)
