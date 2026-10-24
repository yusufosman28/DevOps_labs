# Building and Running Containers

## Overview

Building turns a Dockerfile into an image; running turns an image into a container. A few flags control whether the container runs in the background and whether anything outside it can reach it.

---

## Key Concepts

- **`-t`** gives an image a name (tag) when building.
- **The `.`** at the end of `docker build` tells Docker where the Dockerfile and files are: here.
- **`-d`** (detached) runs a container in the background and returns the prompt.
- **`-p host:container`** publishes a port: traffic to that port on my laptop is forwarded into the container. Without it, the app runs but nothing outside can reach it.
- `EXPOSE` only documents a port; `-p` is what actually makes it reachable.

---

## Commands Practised

```bash
docker build -t hello-flask .                 # build and name the image
docker build -f Dockerfile.full -t hello-flask-full .   # build from a different file
docker images                                 # list images
docker run -d -p 5003:5003 hello-flask        # run in the background, publish port 5003
docker ps                                     # PORTS: 0.0.0.0:5003->5003/tcp
docker stop 8ecea3b686c4                      # first 12 characters of the ID are enough
docker rmi hello-flask-full                   # remove an image to free space
```

Then `http://localhost:5003` in the browser showed the app.

---

> [!WARNING]
> `docker build -t hello-flask` without the final `.` fails with "requires 1 argument". The dot is that argument.

> [!TIP]
> In `docker ps`, an arrow in the PORTS column (`0.0.0.0:5003->5003/tcp`) means published. No arrow (`3306/tcp`) means reachable only inside Docker.

---

## Reflection

`-p` did not click from the explanation alone. It made sense once I ran the container and saw `0.0.0.0:5003->5003/tcp` in `docker ps`: a door from my laptop straight into the container.

⬅️ [Back to Fundamentals](./)
