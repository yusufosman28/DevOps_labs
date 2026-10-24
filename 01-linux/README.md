# Linux

![OS](https://img.shields.io/badge/OS-Linux-blue?logo=linux)
![Distro](https://img.shields.io/badge/Distro-Ubuntu%20(WSL%202)-E95420?logo=ubuntu&logoColor=white)
![Shell](https://img.shields.io/badge/Shell-Bash-4EAA25?logo=gnubash&logoColor=white)
![Practice](https://img.shields.io/badge/Practice-Hands--on-orange)

This folder documents my hands-on learning of **Linux**, from core command-line fundamentals to real problems I hit at the terminal and how I worked through them.

Linux is the foundation of modern infrastructure. Servers, containers, CI/CD runners and cloud platforms all depend on it, so being confident at the command line comes before everything else in DevOps.

My focus throughout has been on **understanding how Linux behaves**, not memorising commands.

---

## Learning Objectives

Through this module, I aimed to:

- Navigate the Linux filesystem confidently from the command line
- Create, move, copy and remove files and directories safely
- Read, search and filter files and command output
- Control where output and errors go using redirection and pipes
- Manage permissions, ownership, users, groups and `sudo`
- Edit files in the terminal with Vim
- Diagnose problems by reading error messages carefully instead of guessing

---

## Topics Covered

### Fundamentals

- [Terminal Basics](./fundamentals/01-terminal-basics.md)  
  Command structure, navigation, and using `man` instead of guessing.

- [Shell Basics](./fundamentals/02-shell-basics.md)  
  How a command reaches the kernel, `PATH`, and switching between bash and zsh.

- [File System](./fundamentals/03-file-system.md)  
  Directory layout, absolute vs relative paths, and working with files and directories.

- [Reading and Searching](./fundamentals/04-reading-and-searching.md)  
  Viewing files and filtering output with `cat`, `head`, `tail` and `grep`.

- [Redirection and Pipes](./fundamentals/05-redirection-and-pipes.md)  
  `stdin`, `stdout`, `stderr`, `/dev/null` and chaining commands.

- [Permissions](./fundamentals/06-permissions.md)  
  Read, write and execute, octal notation, `chmod` and `chown`.

- [Users and Groups](./fundamentals/07-users-and-groups.md)  
  Creating users, managing groups, `sudo` and installing packages.

- [Vim Basics](./fundamentals/08-vim-basics.md)  
  Modes, saving, searching and getting unstuck.

---

### Troubleshooting

- [What Broke and How I Fixed It](./troubleshooting)  
  Real errors from my own terminal sessions, broken down into problem, cause, fix and lesson.

---

## Learning Approach

This folder reflects **how I learn**, not just what I learned.

- Every command practised in a real terminal (Ubuntu on WSL 2)
- Mistakes kept and written up instead of tidied away
- Notes explain **why** a command behaves the way it does
- Concepts revisited later as they came up again in Bash, Git and Docker

---

## Folder Structure

```
01-linux/
├── README.md
├── fundamentals/
│   ├── README.md
│   ├── 01-terminal-basics.md
│   ├── 02-shell-basics.md
│   ├── 03-file-system.md
│   ├── 04-reading-and-searching.md
│   ├── 05-redirection-and-pipes.md
│   ├── 06-permissions.md
│   ├── 07-users-and-groups.md
│   └── 08-vim-basics.md
└── troubleshooting/
    ├── README.md
    ├── 01-sudo-and-redirection.md
    ├── 02-working-in-the-wrong-directory.md
    ├── 03-spacing-errors.md
    └── 04-vim-commands-saved-as-text.md
```
