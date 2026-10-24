# DNS Records and Tools

## Overview

The authoritative server stores a domain's information as records in a zone file. Knowing the record types, where they are managed, and how to query them is what lets me point a domain at a server and check that it worked.

---

## Key Concepts

A record line looks like this:

```
google.com.   300   IN   A   142.250.180.14
```

Name, TTL in seconds, class (`IN`), type, and data.

| Type | Points a name to | Example use |
|---|---|---|
| **A** | an IPv4 address | `example.com → 203.0.113.10` |
| **AAAA** | an IPv6 address | the IPv6 version of an A record |
| **CNAME** | another name (an alias) | `www.example.com → example.com` |
| **MX** | a mail server | lower priority number is tried first |
| **TXT** | any text | proving domain ownership |
| **NS** | the authoritative name servers | which servers hold the zone |

- A **registrar** is where a domain is bought. A **DNS host** runs the name servers holding its records. If they are different companies, the registrar must be told to use the DNS host's NS records.
- **`/etc/hosts`** is a local override, checked before any DNS lookup leaves the machine.

---

## Commands Practised

```bash
nslookup google.com        # simple lookup
dig google.com             # detailed: question, answer, query time
dig +short google.com      # just the IP
dig +short NS google.com   # just the name servers
sudo vim /etc/hosts        # system file, so sudo is needed to edit it
```

A hosts file entry:

```
127.0.0.1   example.com
```

---

> [!IMPORTANT]
> **A points to an IP. CNAME points to another name.** If the server's IP changes, only the A record needs updating and every CNAME follows.

> [!WARNING]
> `127.0.0.1` is localhost, the machine itself. A test line like `127.0.0.1 google.com` left in `/etc/hosts` makes Google fail to load with no obvious error. Remove test entries afterwards.

---

## Reflection

The A vs CNAME distinction is the one I made sure I could explain cleanly: A points to an IP, CNAME points to another name, and getting it wrong breaks a domain.

⬅️ [Back to Fundamentals](./)
