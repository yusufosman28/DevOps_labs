# Multi-Container Applications

## Overview

My first multi-container application was a Flask app that asks a MySQL database for its version and shows it on the page. It brought together networks, names, environment variables and ports.

---

## Key Concepts

- **`--name`** gives a container a fixed name, which other containers use to find it.
- **`--network`** attaches the container to a custom network, so it can be reached by that name.
- **`-e`** passes an environment variable into the container. The MySQL image reads `MYSQL_ROOT_PASSWORD` when it starts.
- **`image:tag`**, such as `mysql:5.7`, is the image and its version.
- Only the web app needs `-p`, because only the browser outside Docker calls it. The database is called by the app, from inside the network.

---

## Commands Practised

```bash
docker network create my-custom-network

docker run -d --name mydb --network my-custom-network \
  -e MYSQL_ROOT_PASSWORD=my-secret-pw mysql:5.7

docker build -t hello-flask-mysql .

docker run -d --name myapp --network my-custom-network \
  -p 5003:5003 hello-flask-mysql
```

The app connects using the container name:

```python
db = MySQLdb.connect(host="mydb", user="root", passwd="my-secret-pw", db="mysql")
```

Result in the browser: `Hello, World! MySQL version: 5.7.44`

---

> [!WARNING]
> Without `-e MYSQL_ROOT_PASSWORD`, the MySQL container refuses to start and exits.

> [!IMPORTANT]
> The course code used port 5002, but my setup uses 5003. Copied code always needs adapting to my own ports and names.

---

## Reflection

Running four separate commands in the right order, with matching names and passwords, showed exactly why Docker Compose exists.

⬅️ [Back to Fundamentals](./)
