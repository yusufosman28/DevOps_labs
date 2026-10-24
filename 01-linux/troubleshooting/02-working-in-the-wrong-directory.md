# Working in the Wrong Directory

## Problem

After one mistyped command, everything started failing: files I had just created were "missing" and writes were refused.

```
$ cat /etc
cat: /etc: Is a directory
$ cat etc
cat: etc: No such file or directory
$ /etc
$ cd ..
$ cat everything.txt
cat: everything.txt: No such file or directory
$ ls missingfile1.txt /etc &> everything.txt
zsh: permission denied: everything.txt
```

---

## Investigation

Each failure looked like a separate problem, so I kept trying fixes for each one. `pwd` finally showed I was in `/`, not my home directory.

---

## Cause

I typed `cat` when I meant `ls`. Then a bare `/etc` (which zsh treats as "change directory") silently moved me into `/etc`, and `cd ..` took me up to `/`. From there, my files were still safe in my home directory, and `/` is not writable by my user.

> [!NOTE]
> Nothing was broken at any point. I had moved without realising.

---

## Fix

```bash
pwd       # confirmed I was in /
cd ~      # back to my home directory
```

The same problem came up later on a new laptop: `cd /docker-learning/hello_flask` failed because the leading `/` starts from the top of the system and skips `/home/yusuf`. The correct path was:

```bash
cd ~/docker-learning/hello_flask
```

---

## What I Learned

- When several commands fail in ways that do not make sense, run `pwd` first
- A leading `/` always means "start from the top of the filesystem"
- After three failed guesses, stop and look (`pwd`, `ls`) instead of trying a fourth

⬅️ [Back to Troubleshooting](./)
