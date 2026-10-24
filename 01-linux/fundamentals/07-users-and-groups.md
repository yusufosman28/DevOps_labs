# Users and Groups

## Overview

Linux is a multi-user system. Users and groups decide who can do what, and `sudo` allows trusted users to carry out admin tasks without logging in as root.

---

## Key Concepts

### `sudo`

`sudo` runs a single command with root privileges. It asks for **my** password, only works for users in the `sudo` group, and every use is logged in `/var/log/auth.log`. It borrows root's permissions for one command; it does not bypass them.

### Groups

Permissions are given to groups, and users inherit them by joining. The "sudoers list" is simply a group called `sudo`.

### Root

`sudo su` switches to the root user entirely. The prompt changes to `#`, which is a warning sign: nothing stops a destructive command from running.

---

## Commands Practised

```bash
sudo adduser newuser              # create a user
sudo passwd newuser               # set their password
su - newuser                      # switch to that user
whoami                            # confirm who I am
exit                              # return to the previous user

sudo groupadd devops              # create a group
sudo usermod -aG devops newuser   # add the user to a group
groups                            # groups the current user is in
grep devops /etc/group            # check a group exists
sudo gpasswd -d newuser devops    # remove the user from a group

sudo tail /var/log/auth.log       # recent sudo activity
```

### Installing software

```bash
sudo apt update                   # refresh the package list
sudo apt install python3-flask    # install a package
```

---

> [!WARNING]
> `usermod -G` without `-a` **replaces** a user's groups instead of adding to them. Running it on my own account could remove me from `sudo` with no way to add myself back.

> [!NOTE]
> Installing without `apt update` first can fail with "package cannot be located", because the package list is out of date.

---

## Reflection

Testing changes by switching into the new user (`su -`, `groups`, `exit`) was more reliable than assuming a command had worked. The `-a` in `usermod -aG` is now something I check every time.

⬅️ [Back to Fundamentals](./)
