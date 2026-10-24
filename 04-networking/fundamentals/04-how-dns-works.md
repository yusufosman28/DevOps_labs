# How DNS Works

## Overview

DNS turns names people can remember, like `google.com`, into IP addresses computers can use. It runs on port 53, mostly over UDP because lookups need to be fast, and almost every connection starts with a DNS lookup.

---

## Key Concepts

### The hierarchy

No single server knows every answer:

1. **Root servers** know where each ending lives (`.com`, `.org`, `.uk`).
2. **TLD servers** know which server is responsible for each domain (`.com` knows about `google.com`).
3. **Authoritative name servers** hold the actual records for a domain.

Reading a name right to left follows the hierarchy: `www.google.com.` → root (the hidden final dot) → `.com` → `google` → `www`.

### Resolver vs authoritative

- The **resolver** (usually the ISP's) does the work of asking each level on my behalf, and caches the answer.
- The **authoritative server** owns the real answer.

### Caching and TTL

Each cached answer has a **TTL** (time to live), set by the domain owner. When it runs out, the next lookup asks again. This stops outdated answers being used forever when an IP changes.

---

## Commands Practised

The lookup, step by step:

```
1. Check my machine's cache and /etc/hosts       → found? done
2. Ask the resolver; it checks its cache         → found? done
3. Resolver asks a root server                   → "ask the .com server"
4. Resolver asks the .com TLD server             → "ask Google's name server"
5. Resolver asks Google's authoritative server   → 142.250.180.14
6. Resolver caches the answer
7. My browser connects to the IP
```

```bash
nslookup google.com    # "Non-authoritative answer" = it came from a cache
```

---

> [!NOTE]
> If a site moves to a new IP but I still reach the old one, the old answer is probably still cached until its TTL expires.

---

## Reflection

The resolver doing all the running around, while owning no answers itself, was the part that made the whole lookup make sense.

⬅️ [Back to Fundamentals](./)
