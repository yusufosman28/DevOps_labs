# `sudo` Did Not Fix "Permission Denied"

## Problem

I was saving a command's output and errors to a file. It had worked earlier, but now it was refused, and adding `sudo` gave exactly the same error.

```
$ ls missingfile1.txt /etc &> everything.txt
zsh: permission denied: everything.txt
$ sudo ls missingfile1.txt /etc &> everything1.txt
zsh: permission denied: everything1.txt
```

---

## Investigation

`sudo` failing in exactly the same way told me the problem was not the `ls` command itself. Running `pwd` showed I was in `/`, a directory my user does not own.

---

## Cause

The **shell** creates the output file before the command runs, and the shell is running as my normal user. `sudo` only elevated `ls`, which was never the part being denied.

> [!IMPORTANT]
> `sudo` applies to the command it is attached to, not to the redirection on the same line.

---

## Fix

Moved back to a directory I own. When writing to a protected location is genuinely needed, the correct approach is `sudo tee`, because `tee` is a command and can be elevated:

```bash
echo "text" | sudo tee /etc/protected-file
```

---

## What I Learned

- The shell handles redirection before the command starts
- `sudo` elevates one command, not the whole line
- An error that does not change when I change the command usually means the problem is somewhere else

⬅️ [Back to Troubleshooting](./)
