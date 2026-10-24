# Docker Compose

## Overview

Docker Compose describes every container in an application, with all its settings, in one file. One command then builds and starts the whole stack. It replaces a list of long commands that had to be typed in the right order.

---

## Key Concepts

- Each container is a **service** in `docker-compose.yml`.
- Compose creates a network automatically and puts every service on it, so services find each other by **service name**.
- **YAML indentation is the structure:** settings belong to a service because they are indented under it.
- The compose file lives in Git next to the code, so anyone who clones the repository can run the whole application with one command.

| Compose line | Replaces |
|---|---|
| service name (`web`, `mydb`) | `--name` |
| `build: .` | `docker build -t ... .` |
| `image: mysql:5.7` | the image in `docker run` |
| `ports:` | `-p` |
| `environment:` | `-e` |
| `depends_on:` | starting containers in the right order |
| (automatic) | `docker network create` and `--network` |

---

## Commands Practised

My compose file:

```yaml
services:
  web:
    build: .
    ports:
      - "5003:5003"
    depends_on:
      - mydb

  mydb:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: my-secret-pw
```

```bash
docker compose up                      # build if needed, start, stream logs
docker compose up -d                   # same, in the background
docker compose up --build              # rebuild images first, after changing code
docker compose logs                    # logs from every service
docker compose down                    # stop and remove containers and the network
docker compose down --remove-orphans   # also remove containers from renamed services
```

---

> [!IMPORTANT]
> After changing application code, plain `docker compose up` reuses the old image, because `COPY . .` copied the old files in at build time. `--build` rebuilds it.

> [!NOTE]
> The `version:` line in older compose files is obsolete. Newer Compose shows a warning and ignores it, so I removed it.

---

## Reflection

Going from four commands to one file made Compose's value obvious. Hitting a service-name mismatch straight away also showed that the names in the file are exactly what the app has to use. That one is written up in [Unknown Server Host](../../04-networking/troubleshooting/02-unknown-server-host.md).

⬅️ [Back to Fundamentals](./)
