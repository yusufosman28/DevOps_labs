# `bad substitution`

## Problem

```
./var.sh: line 8: ${fruits[@}: bad substitution
```

---

## Investigation

The error gave a line number, so I went straight to line 8 and compared what I had typed with the shape it should have.

---

## Cause

```bash
echo ${fruits[@}      # the square bracket was never closed
```

"Bad substitution" means the `${...}` syntax itself is malformed, not that the variable is wrong.

---

## Fix

```bash
echo ${fruits[@]}
```

---

## What I Learned

- The line number in an error message is the fastest route to the problem
- Reading the error message literally, instead of guessing, solved it in seconds
- This was the first error I traced and fixed completely on my own

⬅️ [Back to Troubleshooting](./)
