# Script Basics

## Overview

A Bash script is a text file containing the same commands I would type at the prompt, written so they run together. Getting a script to run depends on three separate things that are easy to confuse: the shebang, the execute permission, and how the script is called.

---

## Key Concepts

- **The shebang** (`#!/bin/bash`) is the first line and names the program that runs the file. Nothing can come above it.
- **Execute permission** (`chmod +x`) allows the file to be run directly. Without it, `./script.sh` returns "permission denied".
- **`./`** means "this folder". Without it, the shell searches `PATH`, does not find the script, and returns "command not found".
- **`bash script.sh`** runs Bash and passes the file to it, so it needs no execute permission and ignores the shebang.
- The `.sh` extension is only a convention; Linux cares about the execute bit.
- `/usr/local/bin` is the conventional folder for scripts I have written myself, because it is already on `PATH`.

---

## Commands Practised

```bash
#!/bin/bash
echo "hello world"
```

```bash
chmod +x greet.sh      # make it executable
./greet.sh             # run the file: needs the execute bit, obeys the shebang
bash greet.sh          # run bash on the file: no execute bit needed
```

Comments:

```bash
# A single-line comment

: '
A multi-line comment.
The space between : and the quote is required.
'
```

Running a script from anywhere:

```bash
sudo mv greet.sh /usr/local/bin/greet && sudo chmod +x /usr/local/bin/greet
which greet            # /usr/local/bin/greet
greet                  # now works from any directory
```

---

> [!NOTE]
> VS Code's Code Runner uses `bash script.sh`, so it skips the execute bit and the shebang. I also run scripts by hand with `./` so those steps stay familiar.

---

## Reflection

Separating the three pieces (what runs the file, whether it is allowed to run, and where the shell looks for it) explained every "permission denied" and "command not found" I hit when starting out.

⬅️ [Back to Fundamentals](./)
