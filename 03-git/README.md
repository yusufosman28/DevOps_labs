# Git

![VCS](https://img.shields.io/badge/VCS-Git-F05032?logo=git&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-GitHub-181717?logo=github&logoColor=white)
![Focus](https://img.shields.io/badge/Focus-Version%20Control-purple)
![Practice](https://img.shields.io/badge/Practice-Hands--on-orange)

This folder documents my hands-on learning of **Git**, from how it stores history to pushing real projects to GitHub, followed by the problems I hit connecting to a remote for the first time.

Git is the starting point of almost every DevOps workflow. Application code, Dockerfiles, Terraform and CI/CD pipelines all live in Git, and every automated deployment begins with a commit.

My focus has been on **understanding what Git is actually doing**, so that commands like `add`, `commit` and `push` make sense rather than being memorised.

---

## Learning Objectives

Through this module, I aimed to:

- Understand how Git stores history as snapshots
- Move changes through the working directory, staging area and repository
- Inspect changes and history with `status`, `diff` and `log`
- Create, switch between and merge branches
- Connect a local repository to GitHub and push to it
- Write commit messages that describe what a change does

---

## Topics Covered

### Fundamentals

- [What Git Is](./fundamentals/01-what-is-git.md)  
  Version control, distributed design, snapshots, and Git vs GitHub.

- [The .git Directory and Terminology](./fundamentals/02-git-directory-and-terminology.md)  
  What lives inside `.git`, and the meaning of commit, branch, HEAD, blob and tree.

- [The Three Areas](./fundamentals/03-the-three-areas.md)  
  Working directory, staging area and repository.

- [Core Commands](./fundamentals/04-core-commands.md)  
  `init`, `status`, `add`, `commit`, `diff` and `log`.

- [Branching](./fundamentals/05-branching.md)  
  Creating and moving between branches with `branch` and `switch`.

- [Merging and History](./fundamentals/06-merging-and-history.md)  
  Fast-forward merges, merge commits, conflicts and viewing history.

- [Remotes and GitHub](./fundamentals/07-remotes-and-github.md)  
  Connecting to GitHub, pushing, cloning and authenticating with tokens.

- [Commit Messages](./fundamentals/08-commit-messages.md)  
  How I write commit messages, and when to commit.

---

### Troubleshooting

- [What Broke and How I Fixed It](./troubleshooting)  
  Real errors from pushing my first project to GitHub, broken down into problem, cause, fix and lesson.

---

## Learning Approach

- Git used for real on my own projects, including [docker-learning](https://github.com/yusufosman28/docker-learning) and this repository
- `git status` run between every step to see exactly what changed
- Every error kept and written up instead of tidied away
- Commit history treated as part of the evidence: one change per commit, with a clear message

---

## Folder Structure

```
03-git/
├── README.md
├── fundamentals/
│   ├── README.md
│   ├── 01-what-is-git.md
│   ├── 02-git-directory-and-terminology.md
│   ├── 03-the-three-areas.md
│   ├── 04-core-commands.md
│   ├── 05-branching.md
│   ├── 06-merging-and-history.md
│   ├── 07-remotes-and-github.md
│   └── 08-commit-messages.md
└── troubleshooting/
    ├── README.md
    ├── 01-wrong-remote-url.md
    ├── 02-password-rejected-on-push.md
    ├── 03-repository-not-found.md
    └── 04-staged-the-wrong-file.md
```
