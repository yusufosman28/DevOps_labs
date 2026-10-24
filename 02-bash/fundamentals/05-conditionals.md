# Conditionals

## Overview

Conditionals let a script make decisions: run one block when something is true and another when it is not. They are behind validation, safety checks and any script that responds to its environment.

---

## Key Concepts

- **`[` is a command.** `if` runs it and checks its exit code (0 = true). That is why `[`, each argument and `]` must be separated by spaces.
- Bash checks `if`/`elif` from the top and runs only the **first** true branch, so the most specific condition goes first.
- Two separate `if` blocks are not the same as an `if`/`elif` chain: separate blocks can both run.
- `[[ ]]` is the newer form, safer with empty variables and patterns.

| Numbers | Meaning |
|---|---|
| `-eq` / `-ne` | equal / not equal |
| `-gt` / `-lt` | greater / less than (strict) |
| `-ge` / `-le` | greater / less than or equal |

| File test | True if |
|---|---|
| `-f` | a regular file |
| `-d` | a directory |
| `-e` | exists at all |
| `-r` / `-w` / `-x` | readable / writable / executable |

---

## Commands Practised

```bash
if [ "$score" -ge 90 ]; then
    echo "Excellent"
elif [ "$score" -ge 80 ]; then
    echo "Good"
else
    echo "Keep going"
fi
```

```bash
if [ "$name" = "Ahmed" ]; then echo "Hi Ahmed"; fi                 # string comparison
if [ "$grade" -ge 90 ] && [ "$grade" -le 100 ]; then echo "A"; fi  # combined conditions
if [ -f config.txt ]; then echo "Config found"; fi                 # file test
```

---

> [!WARNING]
> `>` inside `[ ]` is **redirection**, not "greater than". `[ $age > 18 ]` creates a file called `18` and compares nothing.

---

## Reflection

Learning that `[` is a command made every spacing rule make sense at once, instead of being something to memorise.

⬅️ [Back to Fundamentals](./)
