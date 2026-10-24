# Networking

![Networking](https://img.shields.io/badge/Networking-Computer%20Networks-607D8B?logo=cloudflare&logoColor=white)
![Protocols](https://img.shields.io/badge/Protocols-TCP%2FIP-blue)
![Focus](https://img.shields.io/badge/Focus-Fundamentals-purple)
![Practice](https://img.shields.io/badge/Practice-Hands--on-orange)

This folder documents my learning of **networking** fundamentals, from how data finds its way across the internet to what I saw happening on my own machine while running applications in containers.

Every part of DevOps sits on a network: servers talking to databases, users reaching websites, containers finding each other, and cloud resources inside VPCs. Understanding addressing, ports, DNS and routing makes it possible to debug connection problems instead of guessing.

My focus has been on **understanding how traffic actually flows**, and connecting the theory to what I could see in real command output.

---

## Learning Objectives

Through this module, I aimed to:

- Explain the difference between IP and MAC addresses and how routing uses them
- Understand ports and protocols, and when TCP or UDP is used
- Place problems on the OSI and TCP/IP models
- Explain how a DNS lookup works, from cache to authoritative server
- Read and use DNS records, `/etc/hosts`, `nslookup` and `dig`
- Recognise these concepts in real output when running applications and containers

---

## Topics Covered

### Fundamentals

- [Addresses and Routing](./fundamentals/01-addresses-and-routing.md)  
  IPv4, IPv6, MAC addresses, and how routers decide where traffic goes.

- [Ports and Protocols](./fundamentals/02-ports-and-protocols.md)  
  Common ports, TCP vs UDP, and the three-way handshake.

- [Network Models](./fundamentals/03-network-models.md)  
  The OSI and TCP/IP models and encapsulation.

- [How DNS Works](./fundamentals/04-how-dns-works.md)  
  The DNS hierarchy, the lookup process, resolvers and caching.

- [DNS Records and Tools](./fundamentals/05-dns-records-and-tools.md)  
  Record types, registrars, `/etc/hosts`, `nslookup` and `dig`.

- [Networking in Practice](./fundamentals/06-networking-in-practice.md)  
  Localhost, port mapping, HTTP status codes and name resolution, as I saw them running Flask and Docker.

---

### Troubleshooting

- [What Broke and How I Fixed It](./troubleshooting)  
  Real network-related problems from my own projects, broken down into problem, cause, fix and lesson.

---

## Learning Approach

- Theory tested topic by topic, then revisited when it appeared in real output
- Concepts connected to the tools I use: Flask, Docker networks and Docker Compose

---

## Folder Structure

```
04-networking/
├── README.md
├── fundamentals/
│   ├── README.md
│   ├── 01-addresses-and-routing.md
│   ├── 02-ports-and-protocols.md
│   ├── 03-network-models.md
│   ├── 04-how-dns-works.md
│   ├── 05-dns-records-and-tools.md
│   └── 06-networking-in-practice.md
└── troubleshooting/
    ├── README.md
    ├── 01-browser-showed-a-saved-page.md
    └── 02-unknown-server-host.md
```
