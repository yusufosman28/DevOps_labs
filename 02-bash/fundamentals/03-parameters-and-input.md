# Parameters and User Input

## Overview

Parameters let a script take values when it is run, which turns a fixed script into a reusable tool. `read` does the same thing interactively, by pausing for the user to type.

---

## Key Concepts

| Parameter | Holds |
|---|---|
| `$1`, `$2` | the first and second arguments |
| `$@` | all arguments |
| `$#` | the number of arguments |
| `$0` | the script's own name |

- Arguments are matched by **position**.
- `read` pauses the script and stores what the user types in a variable.
- `$#` lets a script check it received what it needs before acting.

---

## Commands Practised

```bash
./greet.sh hello hi hey    # $1=hello  $2=hi  $#=3
```

```bash
echo "What is your name?"
read name
echo "Hello $name"
```

Using an argument if given, otherwise asking:

```bash
greet() {
    local name
    if [ $# -eq 0 ]; then
        read -p "What is your name? " name
    else
        name=$1
    fi
    echo "Hello $name"
}

greet            # prompts for a name
greet "Sam"      # uses Sam
```

---

> [!WARNING]
> Reading `$3` when only two arguments were passed gives an empty value, not an error. Checking `$#` first avoids running on missing input.

---

## Reflection

`$#` was the piece that made parameters useful: it lets a script check it has what it needs before doing anything.

⬅️ [Back to Fundamentals](./)
