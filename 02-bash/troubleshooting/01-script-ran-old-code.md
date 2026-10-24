# The Script Ran My Old Code

## Problem

I added an `else` branch and changed a variable in `test.sh`, ran it twice, and got exactly the old output both times.

---

## Investigation

I started doubting my logic, then noticed the `●` dot on the VS Code tab next to the file name.

---

## Cause

The dot means **unsaved**. My changes only existed in the editor. The file on disk was still the old version, and Bash only ever runs the file on disk.

---

## Fix

Saved with `Ctrl+S` and ran it again. The new output appeared.

> [!TIP]
> When the output does not match the code in front of me, I check that the machine is running what I think it is before debugging the logic.

---

## What I Learned

- The editor and the disk are two different things
- Check for unsaved changes before debugging
- The same idea came back in Docker: changing a file does nothing until the image is rebuilt

⬅️ [Back to Troubleshooting](./)
