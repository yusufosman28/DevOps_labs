# VMs vs Containers

## Overview

Virtual machines and containers both isolate applications, but at different levels. Knowing the difference explains why containers are fast and light, and when a VM is still the better choice.

---

## Key Concepts

- A **virtual machine** runs a complete guest operating system on top of a hypervisor.
- A **container** brings no operating system of its own. It shares the host's **kernel** and packages only the application and its dependencies.

| | Virtual machine | Container |
|---|---|---|
| Own operating system | yes, a full guest OS | no, shares the host kernel |
| Start time | minutes | seconds |
| Size | heavy | light |
| Isolation | very strong | process-level |
| Portability | lower | high |

- Use a **VM** when complete separation or a **different operating system** is needed. A container on Linux can only run Linux software.
- Use a **container** when speed, density and portability matter.

---

## Commands Practised

```bash
docker info
```

Lines from my own output that show containers sharing the host:

```
Kernel Version: ...microsoft-standard-WSL2   # the host kernel every container uses
OSType: linux                                # so these containers run Linux software
```

---

> [!TIP]
> A one-line interview answer: "A VM runs its own full operating system, so it is heavy and slow to start but strongly isolated. A container shares the host's kernel and packages only the app and what it needs, so it is lightweight, starts in seconds and is easy to move."

---

## Reflection

Seeing the WSL 2 kernel listed in `docker info` turned "containers share the host kernel" from a definition into something I could point at.

⬅️ [Back to Fundamentals](./)
