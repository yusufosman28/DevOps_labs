# The Browser Showed a Saved Page

## Problem

After starting my app with Docker Compose, the browser showed the page I expected:

```
Hello, World! MySQL version: 5.7.44
```

But I had predicted another error, so a working page did not add up.

---

## Investigation

The browser tab had been left open since the day before, from when the app last worked. I forced a fresh request with a hard refresh (`Ctrl + F5`). The page changed to:

```
500 Internal Server Error
```

---

## Cause

The browser was showing a **saved copy** of the page from the previous day. The real app was crashing on every request.

A `500` means the application received the request but failed while handling it, so the problem was inside the app, not in the network path or the port mapping.

---

## Fix

Hard refresh first, then read the application logs to find the real error. That led to the problem in [Unknown Server Host](./02-unknown-server-host.md).

> [!TIP]
> Before trusting a page, use `Ctrl + F5` or open a fresh tab, especially when testing changes.

---

## What I Learned

- What is on screen is not always a fresh response from the server
- When a result contradicts what I expect, check it instead of explaining it away
- A `500` points inside the application; the logs show why

⬅️ [Back to Troubleshooting](./)
