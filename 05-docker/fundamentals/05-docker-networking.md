# Docker Networking

## Overview

Most applications are several containers, such as a web app and a database, that need to talk to each other and sometimes to the outside world. Docker networks decide who can reach whom.

---

## Key Concepts

| Network | What it is | `-p` | Used for |
|---|---|---|---|
| **bridge** | a private network on the machine; each container gets its own IP | needed for outside access | the default; most applications |
| **host** | the container uses the machine's network directly | ignored | rare cases needing direct access to the host network |
| **none** | no network at all | pointless | isolated jobs that must not send anything out |

### Default bridge vs custom bridge

| | Default `bridge` | Custom bridge |
|---|---|---|
| How | no `--network` flag | `docker network create`, then `--network` |
| Containers find each other by | IP address only | **name**, through Docker's built-in DNS |

Container IPs can change on restart, so connecting by name on a custom network is the reliable option.

---

## Commands Practised

```bash
docker network ls
docker network create my-custom-network
```

My `docker network ls` output:

```
NAME                DRIVER    SCOPE
bridge              bridge    local
host                host      local
my-custom-network   bridge    local     # a custom network is still a bridge
none                null      local
```

---

> [!IMPORTANT]
> On the default bridge, `host="mydb"` does not work: there is no name lookup. Names only resolve on a custom network or in Docker Compose.

> [!NOTE]
> `-p` is only for traffic coming from **outside** Docker. Containers on the same network talk to each other directly, with no ports published.

---

## Reflection

Picturing Docker networks as an office phone system (desks with extensions, an internal line, and a directory on custom networks) made it clear why some containers need `-p` and others do not.

⬅️ [Back to Fundamentals](./)
