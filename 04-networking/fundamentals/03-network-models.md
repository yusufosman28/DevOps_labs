# Network Models

## Overview

Network models split communication into layers, so each layer only handles its own job. That separation is what lets a browser work the same over Wi-Fi, cable or fibre, and it gives a structured way to locate where a problem is.

---

## Key Concepts

### OSI model: 7 layers

| Layer | Name | Job | Examples |
|---|---|---|---|
| 1 | Physical | the signal itself | cables, Wi-Fi, fibre |
| 2 | Data Link | hand-off to the next device | MAC addresses, switches |
| 3 | Network | route to the destination | IP addresses, routers |
| 4 | Transport | deliver reliably or quickly | TCP, UDP, ports |
| 5 | Session | open, maintain, close the conversation | session setup |
| 6 | Presentation | translate and encrypt | encryption, formats |
| 7 | Application | what the user interacts with | HTTP, DNS, SMTP |

### TCP/IP model: 4 layers

| TCP/IP layer | OSI layers |
|---|---|
| Application | 5, 6, 7 |
| Transport | 4 |
| Internet | 3 |
| Network Access | 1, 2 |

### Encapsulation

When sending, each layer **wraps** the data from the layer above with its own information: request, then TCP segment, then IP packet, then frame, then signal. When receiving, each layer **removes** the wrapper its partner added, until the application reads the original data.

---

## Commands Practised

Tools and output I have used, placed on the layers they belong to:

| Layer | What I used or saw |
|---|---|
| 7 Application | HTTP status codes (`200`, `404`, `500`), `nslookup`, `dig` |
| 4 Transport | ports in `docker ps` (`5003/tcp`, `3306/tcp`) |
| 3 Network | container IPs (`172.18.0.3`), WSL IP, localhost (`127.0.0.1`) |

---

> [!IMPORTANT]
> If the signal itself is gone (Wi-Fi drops, cable unplugged), the problem is **Layer 1**. Higher layers only matter once there is a working signal.

---

## Reflection

Placing my own tools on the layers made the model useful for debugging, not just something to memorise: it gives an order to check things in, from the signal upwards.

⬅️ [Back to Fundamentals](./)
