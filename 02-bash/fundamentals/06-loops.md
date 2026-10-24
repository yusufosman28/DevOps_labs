# Loops

## Overview

Loops repeat work without repeating code. The choice between `for` and `while` comes down to one question: **can I write the list in advance?**

---

## Key Concepts

- **`for`** walks through a known list: files in a folder, a range of numbers, items in an array.
- **`while`** repeats until a condition becomes false: retries, waiting for a service, login attempts.
- A `while` loop needs something inside it that changes the condition, or it runs forever.
- **`break`** leaves the loop completely. **`continue`** skips to the next pass.

---

## Commands Practised

```bash
for fruit in "${fruits[@]}"; do echo "$fruit"; done     # over an array
for number in {1..5}; do echo "$number"; done           # over a range
for ((i=1; i<=5; i++)); do echo "Number $i"; done       # counting
```

```bash
count=1
while [ "$count" -le 5 ]; do
    echo "Count: $count"
    ((count++))
done
```

```bash
while true; do
    ((count++))
    if [ "$count" -eq 4 ]; then break; fi
done
```

---

> [!WARNING]
> Without `((count++))`, the `while` loop runs forever with no error. `Ctrl+C` stops it.

> [!IMPORTANT]
> In a `while` loop, `continue` can skip the increment if the increment comes after it. `for ((...))` loops avoid this because the increment is part of the loop line.

---

## Reflection

"For loops walk through things, while loops wait for things" is the rule that stopped me mixing them up.

⬅️ [Back to Fundamentals](./)
