# 06 — File System Structure

---

## Scenario

Understanding the Linux file system hierarchy is essential for navigating, configuring, and securing systems as a cybersecurity analyst. This module focused on learning the structure, purpose, and usage of the major Linux directories, from system binaries and user files to configuration and runtime data. A solid grasp of this hierarchy is foundational for system hardening, forensics, and log analysis.

---

## What I Did

- Listed the root directory contents to understand high-level structure:
  ```zsh
  ls -l /
  ```
- Installed and used `tree` for visual hierarchy inspection:
  ```zsh
  sudo apt update && sudo apt install tree
  tree -L 2 /
  ```
- Investigated core directories:
  ```zsh
  ls -ld /bin /sbin /usr /var /etc /home /opt /tmp
  ```
- Compared system and user binaries:
  ```zsh
  ls /bin | head
  ls /usr/bin | head
  ```
- Explored key configuration files:
  ```zsh
  ls /etc
  less /etc/passwd
  less /etc/fstab
  ```
- Navigated variable and log directories:
  ```zsh
  ls -lh /var
  ls -lh /var/log
  ```
- Investigated user home directories:
  ```zsh
  ls -ld /home/*
  ```
- Checked temporary and runtime directories:
  ```zsh
  ls -ld /tmp /run
  ```
  - Verified sticky bit on `/tmp`
- Explored virtual system directories:
  ```zsh
  ls /proc /sys /dev
  mount | column -t
  ```
- Practiced locating files and binaries:
  ```zsh
  which bash
  whereis ssh
  sudo updatedb && locate passwd
  ```
- Bonus challenge: found largest subdirectories in `/var`:
  ```zsh
  sudo du -h /var | sort -hr | head -n 5
  ```

---

## What I Learned

- Each directory in the root file system has a specific role:
  - `/bin`, `/sbin` for essential binaries
  - `/usr/bin` for user-installed applications
  - `/etc` for configuration
  - `/var` for logs and spools
  - `/tmp` for temporary files with restricted deletion
  - `/home` for user-specific data
  - `/proc`, `/sys`, `/dev` for interacting with kernel and devices
- The sticky bit on `/tmp` is a critical security feature
- Tools like `which`, `whereis`, and `locate` speed up system navigation
- `tree` and `du` are great for understanding hierarchy and usage

---

## Why It Matters

Every SOC analyst and Linux operator must be able to move confidently through the file system. Whether investigating suspicious behavior, setting permissions, collecting forensic artifacts, or writing automation scripts, knowing where things live is critical. This module built the spatial awareness needed to efficiently navigate and manage a Linux system under pressure.

---
