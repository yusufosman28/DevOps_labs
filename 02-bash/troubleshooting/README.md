# Troubleshooting: What Broke and How I Fixed It

![Practice](https://img.shields.io/badge/Practice-Troubleshooting-red)
![Script](https://img.shields.io/badge/Script-Bash-4EAA25?logo=gnubash&logoColor=white)

Real problems from writing my own scripts.

Several of these produced **no error at all**: the script simply did the wrong thing. Those are the most dangerous kind of bug, and the reason I now test edge cases on purpose.

Each write-up covers the **problem**, how I **investigated** it, the **cause**, the **fix** and **what I learned**.

---

## Write-ups

1. [The script ran my old code](./01-script-ran-old-code.md)  
   The editor and the file on disk were out of sync.

2. [The wrong branch ran with no error](./02-wrong-branch-no-error.md)  
   A strict comparison at a boundary value.

3. [A syntax error that stayed hidden](./03-hidden-syntax-error.md)  
   Bash only checks the lines it runs.

4. [`bad substitution`](./04-bad-substitution.md)  
   Tracing an error from its line number.

5. [A comment in the wrong place](./05-comment-in-the-wrong-place.md)  
   Why `#` disables only what is to its right.

⬅️ [Back to Bash](../)
