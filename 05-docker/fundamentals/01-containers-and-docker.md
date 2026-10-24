# Containers and Docker

## Overview

An application never runs on its own: it needs a specific language version, libraries and settings. Move it to a machine missing any of those and it breaks. A container packages the application with everything it needs, so it runs the same anywhere.

---

## Key Concepts

### Docker's main parts

| Part | Job |
|---|---|
| **Docker Engine** | builds and runs containers |
| **Docker Hub** | a public registry of ready-made images |
| **Docker Compose** | runs several containers together as one application |

### Dockerfile → image → container

| | What it is |
|---|---|
| **Dockerfile** | the instructions for building an image |
| **Image** | the built, read-only package: the app plus everything it needs |
| **Container** | a running instance of an image |

One image can start many containers. Images are never edited; a change means building a new image.

### Why containers matter

- **Isolation:** two apps needing different versions of the same library run side by side without clashing.
- **Consistency:** the same image runs the same way on a laptop, in testing and in production, ending "it works on my machine".
- **Efficiency:** no full operating system per container, so they start in seconds and many fit on one machine.

---

## Commands Practised

Checking Docker on my laptop (Docker Desktop with WSL 2 integration):

```bash
docker --version          # Docker version 29.9.1
docker info               # detailed health report
docker run hello-world    # pull and run a test container
docker ps                 # running containers
docker ps -a              # all containers, including stopped ones
```

What `docker run hello-world` did:

```
Unable to find image 'hello-world:latest' locally   # checked my machine first
Pulling from library/hello-world                    # downloaded it from Docker Hub
Hello from Docker!                                  # ran it
```

The container then stopped by itself, which is why `docker ps` was empty and `docker ps -a` showed `Exited (0)`.

---

> [!NOTE]
> On Windows, Docker runs through Docker Desktop. Without **WSL integration** switched on for Ubuntu, `docker` in the Ubuntu terminal returns "command not found".

---

## Reflection

The recipe, frozen meal and plate picture (Dockerfile, image, container) made the three terms stick. It also made it obvious why you rebuild an image instead of editing it.

⬅️ [Back to Fundamentals](./)
