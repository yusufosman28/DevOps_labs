# Networking in Practice

## Overview

The networking theory came alive once I started running applications in containers. Localhost, ports, HTTP status codes and DNS all showed up in real output, and understanding them was the difference between fixing a problem and guessing.

---

## Key Concepts

- **`127.0.0.1` vs `0.0.0.0`:** `127.0.0.1` answers only the machine itself. `0.0.0.0` answers on every address the machine has, which a containerised app needs so traffic from outside the container can reach it.
- **Port mapping:** `-p host:container` forwards a port on my laptop to a port inside a container. Only traffic from **outside** needs it; containers on the same network reach each other directly.
- **Name resolution in Docker:** on a custom bridge network or in Docker Compose, Docker runs its own small DNS, so containers find each other by name. On the default bridge network, they can only use IP addresses.
- **HTTP status codes:** `200` success, `404` not found, `500` the application received the request but crashed while handling it.

---

## Commands Practised

```python
app.run(host='0.0.0.0', port=5003)    # answer on every interface, port 5003
```

```bash
docker network create my-custom-network
docker run -d --name mydb --network my-custom-network -e MYSQL_ROOT_PASSWORD=... mysql:5.7
docker run -d --name myapp --network my-custom-network -p 5003:5003 hello-flask-mysql
```

- `myapp` connects to the database with `host="mydb"`: Docker's DNS turns the name into the container's IP.
- Only `myapp` has `-p`, because only my browser, outside Docker, needs to reach it.

Requests seen in the Flask output:

```
"GET / HTTP/1.1" 200              # my browser visit, successful
"GET /favicon.ico HTTP/1.1" 404   # browser asking for a tab icon the app does not have
```

---

> [!TIP]
> An unpublished database port cannot be reached from outside at all. It is the same thinking as an AWS security group: open only what needs to be open.

---

## Reflection

My own `docker ps` and `docker logs` output ended up being the best networking revision I did. Every concept from the theory appeared there in a form I could check.

⬅️ [Back to Fundamentals](./)
