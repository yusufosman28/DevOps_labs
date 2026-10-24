# Functions

## Overview

Functions group code under a name so it can be reused and tested on its own. They take parameters the same way scripts do and report success or failure with a return code.

---

## Key Concepts

- Defining a function only stores it. Nothing runs until the function is **called**.
- Functions read arguments with `$1`, `$2` and `$#`, like scripts.
- **`local`** keeps a variable inside the function so functions do not overwrite each other's values.
- **`return 1`** stops the function and reports failure; the caller checks it with `$?`.
- **`=~`** checks a value against a pattern. `^[0-9]+$` means digits only, from start to finish.

---

## Commands Practised

```bash
greet() {
    local name=$1
    echo "Hello $name"
}

greet "Ahmed"
```

Validating input:

```bash
validate_age() {
    local age=$1
    if ! [[ "$age" =~ ^[0-9]+$ ]]; then
        echo "Invalid age"
        return 1
    fi
    if [ "$age" -lt 18 ]; then
        echo "Must be at least 18"
        return 1
    fi
    echo "Eligible"
}

validate_age "$user_age"
exit_code=$?
if [ "$exit_code" -ne 0 ]; then
    echo "Validation failed"
fi
```

---

> [!TIP]
> Rejecting bad input early with a clear message is safer than letting a script carry on with the wrong value.

---

## Reflection

Writing validation as its own function made it easier to test edge cases one at a time: letters, empty input and boundary values.

⬅️ [Back to Fundamentals](./)
