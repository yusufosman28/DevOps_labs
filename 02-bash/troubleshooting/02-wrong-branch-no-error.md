# The Wrong Branch Ran With No Error

## Problem

```bash
age=18
if [ $age -gt 18 ]; then
    echo "adult"
else
    echo "not an adult"
fi
```

I expected `adult` and got `not an adult`. There was no error message.

---

## Investigation

The script ran cleanly, so the problem had to be the logic. I checked the comparison operator against the value I was testing.

---

## Cause

`-gt` means **strictly** greater than. 18 is not greater than 18.

---

## Fix

```bash
if [ $age -ge 18 ]; then
```

`-ge` means greater than **or equal to**.

> [!IMPORTANT]
> Comparison mistakes never produce errors. They silently take the wrong path.

---

## What I Learned

- `-gt`/`-lt` are strict; `-ge`/`-le` include the boundary
- Always test the boundary value itself, not just values clearly above and below it

⬅️ [Back to Troubleshooting](./)
