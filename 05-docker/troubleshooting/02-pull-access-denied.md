# Pull Access Denied

## Problem

Straight after the failed build, I tried to run the image:

```bash
docker run -d --name myapp --network my-custom-network -p 5003:5003 hello-flask-mysql
```

```
Unable to find image 'hello-flask-mysql:latest' locally
pull access denied ... repository does not exist
```

---

## Investigation

The build output just before this had failed, with a red error marker on the prompt. The two errors were connected.

---

## Cause

The build had failed, so the image `hello-flask-mysql` was never created. Docker looked for it locally, did not find it, then looked on Docker Hub, where nobody had ever published an image with that name.

This was **one error, not two**: the second was a knock-on effect of the first.

---

## Fix

Fixed the build first (see [`mysqlclient` build failed](./01-mysqlclient-build-failed.md)), then ran the same `docker run` command. It worked.

> [!IMPORTANT]
> When several errors appear in a row, fix the first one. The rest are often consequences of it.

---

## What I Learned

- No successful build means no image, and every command that needs the image fails
- Docker checks locally first, then the registry
- Check that a command succeeded before running the next one

⬅️ [Back to Troubleshooting](./)
