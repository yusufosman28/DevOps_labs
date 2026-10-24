# Variables and Quoting

## Overview

Variables store values so a script can reuse them. Bash is strict about how they are set, read and quoted, and most mistakes here fail silently rather than with a clear error.

---

## Key Concepts

- A variable is set with `name=value` and read with `$name`.
- There must be **no spaces** around `=`.
- **Double quotes** expand variables; **single quotes** keep text exactly as written.
- **Interpolation** inserts a variable's value into surrounding text.
- **Arrays** hold several values. Positions start at 0, and reading them needs curly braces.

---

## Commands Practised

```bash
name="Yusuf Osman"      # quoted because it contains a space
count=28
echo "$name"            # Yusuf Osman
echo "Hello, $USER"     # interpolation
```

```bash
echo "$name"            # Yusuf Osman - double quotes expand
echo '$name'            # $name       - single quotes are literal
```

```bash
fruits=(apple banana orange)
echo "${fruits[@]}"     # all items
echo "${fruits[1]}"     # banana
echo "${#fruits[@]}"    # 3, the number of items
```

---

> [!WARNING]
> `greeting = "hello"` fails with `greeting: command not found`. The spaces make the shell treat `greeting` as a command.

> [!IMPORTANT]
> `$fruits[0]` prints the first item followed by the literal text `[0]`. Arrays need `${fruits[0]}`.

---

## Reflection

Quoting felt like style at first. It is actually how I control what the shell expands and where it splits text, which matters as soon as values contain spaces.

⬅️ [Back to Fundamentals](./)
