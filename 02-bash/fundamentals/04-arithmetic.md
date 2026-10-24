# Arithmetic and Command Substitution

## Overview

By default, Bash treats everything as text, so `5+10` stays the string `5+10`. Arithmetic expansion switches on maths mode. Command substitution looks similar but does something different: it runs a command and uses its output.

---

## Key Concepts

- **`$(( ))`** performs arithmetic. Variables inside do not need `$`, and spaces are allowed.
- `*` means multiply inside `$(( ))`, and `%` gives the remainder.
- Bash arithmetic is **whole numbers only**.
- **`$( )`** runs a command and puts its output in place.

---

## Commands Practised

```bash
num1=5
num2=10
result=$((num1 + num2))     # 15
area=$((length * width))
echo $((10 % 3))            # 1
echo $((10 / 3))            # 3, not 3.33
```

```bash
today=$(date)
echo "Today is $today"

for number in $(seq 1 5); do echo "$number"; done
```

---

> [!WARNING]
> `$((10 / 3))` returns `3` with no rounding and no warning. Decimals need a tool such as `bc` or `awk`.

> [!TIP]
> `$(( ))` does maths. `$( )` runs a command. One extra pair of brackets changes the meaning completely.

---

## Reflection

The silent integer division is the one to remember: percentages and averages come out wrong without any error.

⬅️ [Back to Fundamentals](./)
