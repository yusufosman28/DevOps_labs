# DevOps Labs

![Linux](https://img.shields.io/badge/OS-Linux-blue?logo=linux)
![Bash](https://img.shields.io/badge/Script-Bash-4EAA25?logo=gnubash&logoColor=white)
![Git](https://img.shields.io/badge/VCS-Git-F05032?logo=git&logoColor=white)
![Networking](https://img.shields.io/badge/Networking-TCP%2FIP%20%26%20DNS-607D8B)
![Docker](https://img.shields.io/badge/Containers-Docker-2496ED?logo=docker&logoColor=white)
![Practice](https://img.shields.io/badge/Practice-Hands--on-orange)

This repository documents my hands-on learning across core **DevOps** technologies: the concepts, the commands I practised, and the real problems I hit and fixed along the way.

Every module is built from practice in a real terminal. Errors are kept and written up rather than tidied away, because diagnosing what went wrong is as much a part of the job as getting things to work.

---

## Modules

### [Linux](./01-linux)

Core command-line fundamentals and system administration.

Covers:
- How commands run: shell, kernel and `PATH`
- Navigating the filesystem and managing files
- Reading and filtering output with `grep`, `head` and `tail`
- Redirection, pipes and standard streams
- Permissions, ownership, users, groups and `sudo`
- Editing files with Vim

➡️ [Fundamentals](./01-linux/fundamentals) · [Troubleshooting](./01-linux/troubleshooting)

---

### [Bash Scripting](./02-bash)

Writing scripts that automate tasks and fail safely.

Covers:
- Script structure, permissions and running scripts from anywhere
- Variables, quoting, arrays and parameters
- Conditionals, file tests and loops
- Functions and input validation
- Exit codes and `set -euo pipefail`
- Environment variables and `PATH`

➡️ [Fundamentals](./02-bash/fundamentals) · [Troubleshooting](./02-bash/troubleshooting)

---

### [Git](./03-git)

Version control and working with GitHub.

Covers:
- How Git stores history as snapshots
- The working directory, staging area and repository
- Inspecting changes with `status`, `diff` and `log`
- Branching and merging
- Remotes, pushing and token authentication
- Writing clear commit messages

➡️ [Fundamentals](./03-git/fundamentals) · [Troubleshooting](./03-git/troubleshooting)

---

### [Networking](./04-networking)

How traffic finds its way, from addresses to DNS.

Covers:
- IP and MAC addresses and routing
- Ports, TCP vs UDP and the three-way handshake
- The OSI and TCP/IP models
- How DNS lookups work, record types, `nslookup` and `dig`
- Networking concepts in practice with Flask and Docker

➡️ [Fundamentals](./04-networking/fundamentals) · [Troubleshooting](./04-networking/troubleshooting)

---

### [Docker](./05-docker)

Containerising applications and running them together.

Covers:
- Containers vs virtual machines
- Writing Dockerfiles, layers, caching and slim images
- Building, running and publishing ports
- Docker networks and container-to-container communication
- Logs and exit codes
- Docker Compose for multi-container applications
- Pushing and pulling images with Docker Hub

➡️ [Fundamentals](./05-docker/fundamentals) · [Troubleshooting](./05-docker/troubleshooting) · [Project code](https://github.com/yusufosman28/docker-learning) · [Docker Hub image](https://hub.docker.com/r/yusufosman1280/flask-mysql)

---

## How Each Module Is Organised

Every module follows the same structure, so any folder can be read the same way.

**Fundamentals** - one file per topic, each with:
- **Overview** - what the topic is and why it matters
- **Key Concepts** - the ideas behind it
- **Commands Practised** - real commands and output from my own work
- **Reflection** - what clicked and what I would do differently

**Troubleshooting** - real problems I hit, each written up as:
- **Problem** - what happened and the exact output
- **Investigation** - how I worked out what was going on
- **Cause** - the real reason, which was often not what the error suggested
- **Fix** - what I changed
- **What I Learned** - the lesson I carried forward

---

## Environment

Ubuntu on WSL 2 (Windows) · Bash · VS Code · Docker Desktop · Git and GitHub

---

## Repository Structure

```
DevOps_labs/
├── 01-linux/
├── 02-bash/
├── 03-git/
├── 04-networking/
└── 05-docker/
```

Each module contains a `README.md`, a `fundamentals/` folder and a `troubleshooting/` folder.
