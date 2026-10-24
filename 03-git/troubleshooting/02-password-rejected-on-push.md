# Password Rejected on Push

## Problem

When `git push` asked for a password, I entered my GitHub account password and the push was refused.

---

## Investigation

The username was correct and the password was correct for the GitHub website, so the problem had to be how GitHub accepts credentials from the terminal.

---

## Cause

GitHub no longer accepts account passwords for Git operations in the terminal. It requires a **personal access token** instead.

---

## Fix

1. Created a **personal access token (classic)** on GitHub with the `repo` scope and a 90-day expiry
2. Pasted the token when Git asked for the password (once; pasting it twice also fails)
3. Later signed in to GitHub through VS Code, so pushes from the VS Code terminal no longer ask

> [!WARNING]
> A token is a password. It should never be committed to a repository or shared.

---

## What I Learned

- The terminal and the website authenticate differently
- Tokens can be limited in scope and set to expire, which is safer than a password
- Signing in through VS Code avoids pasting the token every time

⬅️ [Back to Troubleshooting](./)
