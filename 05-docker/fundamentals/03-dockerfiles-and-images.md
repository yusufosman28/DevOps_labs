# Dockerfiles and Images

## Overview

A Dockerfile is a plain text file of instructions that Docker follows, top to bottom, to build an image. Each instruction creates a layer, and understanding layers explains build speed, caching and image size.

---

## Key Concepts

| Instruction | What it does |
|---|---|
| `FROM` | sets the base image; always the first line |
| `WORKDIR` | creates a working folder inside the image and moves into it |
| `COPY . .` | copies files from my folder (first `.`) into the working folder (second `.`) |
| `RUN` | runs a command at **build time**; the result is saved in the image |
| `EXPOSE` | documents the port the app listens on; it does not open it |
| `CMD` | the command run **every time** a container starts |

- **`RUN` vs `CMD`** is about timing: `RUN` happens once while building; `CMD` happens on every start.
- **Layers and caching:** each instruction is a layer. When a line changes, Docker rebuilds from that line down and reuses (`CACHED`) everything above it.
- **Order matters:** instructions that change rarely, such as installing packages, belong above those that change often, such as copying application code.
- **Slim images** (`python:3.12-slim`) leave out tools the app does not need, so they are smaller, faster to pull and have less to patch.

---

## Commands Practised

My Dockerfile for a Flask app that connects to MySQL:

```dockerfile
FROM python:3.12-slim
WORKDIR /app
COPY . .
RUN apt-get update && apt-get install -y gcc pkg-config default-libmysqlclient-dev
RUN pip install flask mysqlclient
EXPOSE 5003
CMD ["python", "app.py"]
```

### Measured: slim vs full base image

I built the same app twice, changing only the `FROM` line:

| Base image | Image size |
|---|---|
| `python:3.12` | 418 MB |
| `python:3.12-slim` | 49.1 MB |

The slim image was about **88% smaller**.

---

> [!WARNING]
> The file must be named exactly `Dockerfile`, with a capital D and no extension.

> [!IMPORTANT]
> Only one `CMD` takes effect. If there are two, the last one wins.

---

## Reflection

Measuring the size difference myself made the case for slim images far more convincing than reading about it. It also explained my first broken build: slim images are small precisely because they leave tools out.

⬅️ [Back to Fundamentals](./)
