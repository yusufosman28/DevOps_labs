# Registries and Docker Hub

## Overview

A registry stores and shares images by name and tag. The Dockerfile lives in Git; the built image lives in a registry, where other machines, teammates and production servers can pull it.

---

## Key Concepts

- **Public registry:** Docker Hub, where images like `mysql:5.7` and `python:3.12-slim` come from.
- **Private registry:** for example Amazon ECR, where only people given access can push or pull.
- Docker looks for an image **locally first**, then in the registry.
- Pushing requires being logged in, and the image name must include the account: `username/repository:tag`.
- Images upload and download as **layers**. Layers that already exist are skipped.
- **Workflow:** build → test → push → pull. Production pulls the exact image that was tested instead of rebuilding it.

---

## Commands Practised

Publishing my Flask and MySQL image to Docker Hub:

```bash
docker login
docker build -t yusufosman1280/flask-mysql:v1 .
docker push yusufosman1280/flask-mysql:v1
```

Proving the round trip by removing the local copy and pulling it back:

```bash
docker rmi yusufosman1280/flask-mysql:v1
docker pull yusufosman1280/flask-mysql:v1
```

```
...: Pull complete       # layers downloaded from Docker Hub
...: Already exists      # layers my laptop already had from other images
Status: Downloaded newer image for yusufosman1280/flask-mysql:v1
```

The repository shows the image as `v1`, at **138.8 MB**.

---

> [!TIP]
> Pulling an image that is already on the machine proves nothing; it just reports "Image is up to date". Removing the local copy first shows the download really works.

> [!NOTE]
> The username in the image name decides which account it goes to. My Docker Hub username is different from my GitHub username, so this has to be right.

---

## Reflection

Seeing "Already exists" next to "Pull complete" explained layers better than any diagram: Docker only moves what has changed.

⬅️ [Back to Fundamentals](./)
