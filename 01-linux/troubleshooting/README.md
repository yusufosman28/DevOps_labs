# Troubleshooting: What Broke and How I Fixed It

![Practice](https://img.shields.io/badge/Practice-Troubleshooting-red)
![Shell](https://img.shields.io/badge/Shell-Bash%20%2F%20Zsh-4EAA25?logo=gnubash&logoColor=white)

Real problems from my own terminal sessions, kept rather than tidied away.

In almost every case, the error message pointed somewhere other than the real cause. The skill was reading past the message to work out what the shell was actually doing.

Each write-up covers:

- The **problem** and the exact output I saw
- How I **investigated** it
- The **cause**
- The **fix**
- **What I learned**

---

## Write-ups

1. [`sudo` did not fix "permission denied"](./01-sudo-and-redirection.md)  
   Why `sudo` does not apply to a redirection.

2. [Working in the wrong directory](./02-working-in-the-wrong-directory.md)  
   Eight confusing errors caused by one silent change of directory.

3. [Errors caused by spacing](./03-spacing-errors.md)  
   One shell rule behind three different failures.

4. [Vim commands saved as text](./04-vim-commands-saved-as-text.md)  
   Typing commands in the wrong mode.

⬅️ [Back to Linux](../)
