# Troubleshooting: What Broke and How I Fixed It

![Practice](https://img.shields.io/badge/Practice-Troubleshooting-red)
![VCS](https://img.shields.io/badge/VCS-Git-F05032?logo=git&logoColor=white)

Real problems from pushing my first project, `docker-learning`, to GitHub from a new laptop.

The push failed four different ways before it worked. Each error pointed at one piece of how remotes and authentication work.

Each write-up covers the **problem**, how I **investigated** it, the **cause**, the **fix** and **what I learned**.

---

## Write-ups

1. [Wrong remote URL](./01-wrong-remote-url.md)  
   A typo in the remote, and why `remote add` would not fix it.

2. [Password rejected on push](./02-password-rejected-on-push.md)  
   GitHub's switch from passwords to tokens.

3. [Repository not found](./03-repository-not-found.md)  
   Pushing to a repository that did not exist yet.

4. [Staged the wrong file](./04-staged-the-wrong-file.md)  
   Why `git status` comes before every commit.

⬅️ [Back to Git](../)
