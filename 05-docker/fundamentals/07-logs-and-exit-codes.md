# Logs and Exit Codes

## Overview

When a container misbehaves, its logs show what the application printed, including errors. When it stops, its exit code shows how it ended. Together they are the first place to look when debugging.

---

## Key Concepts

- **`docker logs`** shows a container's output, whether it is running or has crashed. Build errors are different: they appear during `docker build`.
- Read for the **last meaningful line**; it usually says whether the service is up or why it died.
- `[Warning]` lines are not failures. `ready for connections` from MySQL means the database is up.
- **`docker stop`** asks a container to shut down, waits 10 seconds, then forces it.

| Exit code | Meaning | Seen when |
|---|---|---|
| `0` | finished cleanly | MySQL shut itself down on request |
| `1` | general failure | a failed command |
| `127` | command not found | a missing build tool |
| `137` | killed by force | the Flask dev server ignored the stop request |

---

## Commands Practised

```bash
docker logs myapp
docker logs mydb
docker stop myapp mydb     # several containers in one command
docker ps -a               # mydb: Exited (0), myapp: Exited (137)
docker start mydb          # bring a stopped container back
```

Lines from my logs:

```
Running on http://172.18.0.3:5003                                  # myapp's IP on the custom network
mysqld: ready for connections ... Version: '5.7.44' ... port: 3306  # database is up
```

---

> [!TIP]
> Use my own container names from `docker ps`, not the names used in a tutorial. The wrong name returns "No such container".

---

## Reflection

`Exited (137)` looked alarming until I understood it: nothing was broken, the dev server just did not respond to the polite stop, so Docker forced it.

⬅️ [Back to Fundamentals](./)
