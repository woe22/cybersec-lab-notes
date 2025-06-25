# 03 — Permissions and Users

---

## Scenario

Understanding Linux file permissions and user/group management is essential for system security. This module focused on interpreting and modifying file access permissions, managing user and group accounts, and working with special permission bits like SUID, SGID, and the sticky bit. These skills directly support SOC responsibilities like privilege auditing and securing sensitive files and services.

---

## What I Did

- Investigated file permissions:
  ```zsh
  ls -l /bin/bash
  ```
- Practiced modifying permissions on a test file:
  ```zsh
  touch test.txt
  chmod 644 test.txt
  chmod 600 test.txt
  chmod +x test.txt
  ls -l test.txt
  ```
- Changed file ownership:
  ```zsh
  sudo chown root:root test.txt
  sudo chown $USER:$USER test.txt
  ```
- Explored user and group definitions:
  ```zsh
  cat /etc/passwd | grep '/home'
  cat /etc/group | less
  id
  groups
  ```
- Created and inspected users and groups:
  ```zsh
  sudo groupadd testgroup
  sudo useradd -m -G testgroup testuser
  sudo passwd testuser
  grep testuser /etc/passwd
  grep testgroup /etc/group
  ```
- Resolved a UID_MAX/GID_MAX parsing error in `/etc/login.defs` by removing inline comments
- Explored special permissions:
  ```zsh
  mkdir /tmp/permtest
  sudo chmod +t /tmp/permtest
  ls -ld /tmp/permtest

  sudo chmod u+s /bin/ping
  ls -l /bin/ping

  sudo chmod g+s /usr/bin/wall
  ls -l /usr/bin/wall
  ```
- Cleaned up:
  ```zsh
  sudo userdel -r testuser
  sudo groupdel testgroup
  rm test.txt
  ```

---

## What I Learned

- How Linux file permission bits (`rwx`) work and how to translate them to numeric modes (`644`, `755`)
- Ownership can be modified using `chown` and `chgrp`
- Users and groups are defined in `/etc/passwd` and `/etc/group`
- The sticky bit (`+t`) restricts deletion in shared directories like `/tmp`
- SUID (`+s` on user) and SGID (`+s` on group) elevate privilege during binary execution
- Parsing errors in config files like `/etc/login.defs` can silently break user management tools
- It's important to test and clean up changes when creating test users/groups

---

## Why It Matters

Improper permissions and user mismanagement are among the most common security misconfigurations. This module provided direct, practical experience in setting and auditing file and account access controls — a core responsibility of SOC analysts and system administrators. Understanding how to enforce and evaluate Linux permissions strengthens host-level defense, privilege management, and incident response capabilities.

---

