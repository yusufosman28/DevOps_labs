# Ports and Protocols

## Overview

An IP address gets traffic to the right machine; a port gets it to the right service on that machine. The protocol decides how the data is delivered: reliably, or quickly.

---

## Key Concepts

- **Port:** a numbered entry point to a service, from 0 to 65535. A full destination is IP plus port, such as `142.250.180.14:443`.
- **Protocol:** the rules for the conversation behind that port.

| Port | Service |
|---|---|
| 22 | SSH |
| 25 | SMTP (sending email) |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |
| 3306 | MySQL |
| 5432 | PostgreSQL |

### TCP vs UDP

| | TCP | UDP |
|---|---|---|
| Connection set up first | yes | no |
| Lost data resent | yes | no |
| Speed | slower | faster |
| Used for | websites, email, file downloads | video calls, streaming, gaming, DNS |

### The three-way handshake (TCP)

1. **SYN**: "I want to connect."
2. **SYN-ACK**: "I want to connect too, and I received your message."
3. **ACK**: "Received. Let's go."

---

## Commands Practised

Publishing a container's port to my laptop, and reading the result:

```bash
docker run -d -p 5003:5003 hello-flask
docker ps
```

```
PORTS
0.0.0.0:5003->5003/tcp     # published: laptop port 5003 forwards to container port 5003
3306/tcp                   # MySQL container: port open inside, not published
```

---

> [!TIP]
> A video call that **freezes** is waiting for missing data (TCP behaviour). One that **glitches and carries on** has dropped data (UDP). Calls use UDP because a blurry second beats a frozen call.

> [!NOTE]
> SYN-ACK is both words together because the server does two jobs at once: acknowledging my request and sending its own.

---

## Reflection

Ports stopped being abstract when I saw `0.0.0.0:5003->5003/tcp` next to `3306/tcp` in my own `docker ps` output: one service reachable from my browser, one deliberately kept internal.

⬅️ [Back to Fundamentals](./)
