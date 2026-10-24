# Unknown Server Host

## Problem

My Flask app returned `500 Internal Server Error` when running with Docker Compose, although the same app had worked when I started the containers by hand.

---

## Investigation

I opened a second terminal and read the logs from the web container:

```
web-1 | MySQLdb.OperationalError: (2005, "Unknown server host 'mydb' (-2)")
web-1 | "GET / HTTP/1.1" 500
```

The app could not turn the name `mydb` into an IP address.

---

## Cause

The app connects with `host="mydb"`. In my compose file, I had named the database service `db`. Docker Compose registers each service under its **service name** in its built-in DNS, so a container called `mydb` did not exist.

This was a DNS failure inside Docker: the same job as internet DNS, turning a name into an IP address, but on the network Compose creates.

---

## Fix

Renamed the service to match what the app asks for:

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
```

After a fresh request, the page loaded: `Hello, World! MySQL version: 5.7.44`.

> [!NOTE]
> The other option was to change the app to `host="db"`, but that would have needed an image rebuild. Renaming the service changed only the compose file.

---

## What I Learned

- Containers on a Compose network find each other by service name
- "Unknown server host" means the name lookup failed, not the connection
- The logs pointed straight at the cause once I read them instead of guessing

⬅️ [Back to Troubleshooting](./)
