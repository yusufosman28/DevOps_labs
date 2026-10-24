# Commit Messages

## Overview

The commit history is a record other people read: reviewers, teammates, and anyone trying to work out when something changed. A clear message saves them from opening every file to find out.

---

## Key Concepts

- Short, lowercase, starting with a verb.
- Say **what the change does**, not which file changed.
- Cover the **whole** change, not just part of it.
- One logical change per commit.
- **Do not commit a broken state.** Save the work, and commit only once it builds and runs.

---

## Commands Practised

```bash
git commit -m "connect flask app to mysql and add build tools"
git commit -m "add docker compose file to run flask and mysql together"
git commit -m "add linux fundamentals and troubleshooting"
```

Messages I rewrote:

| First attempt | Problem | Rewritten |
|---|---|---|
| `Add MySQL` | covers half the change | `connect flask app to mysql and add build tools` |
| `Add docker compose yml file` | names the file, not what it does | `add docker compose file to run flask and mysql together` |

---

> [!WARNING]
> `-m` sets the commit message. I once typed `-t`, which is Docker's tag flag, not Git's.

---

## Reflection

Writing the message forces me to describe what the change actually does. If I cannot say it in one line, the commit is probably doing too much.

⬅️ [Back to Fundamentals](./)
