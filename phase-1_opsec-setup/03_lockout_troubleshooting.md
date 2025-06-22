    # 03 — Password Hygiene

---

## Scenario

After setting up my Kali Linux VM and beginning work on password hygiene best practices, I encountered a real-world system lockout situation. While attempting to harden password policies using PAM configuration files, I lost the ability to log in to both the default user and any newly created accounts. This lab captures the misstep, the diagnosis, and the full recovery process.

---

## What I Did

- Attempted to reset the login password via GRUB using `init=/bin/bash`
- Changed the password using `passwd kali`, confirmed success
- Rebooted but still received "Incorrect password" errors
- Created a `rescue` user and reset its password — still failed
- Suspected corruption or misconfiguration of PAM stack
- Rebooted into GRUB, mounted root as read/write:
  ```bash
  mount -o remount,rw /
  ```
- Replaced three critical PAM configuration files with known-safe defaults:
  - `/etc/pam.d/common-auth`
  - `/etc/pam.d/common-password`
  - `/etc/pam.d/login`
- Rebooted system using:
  ```bash
  exec /sbin/init
  ```
- Successfully logged in using `rescue` and original user accounts

---

## What I Learned

> ⏱️ **Lockout Duration:** Approximately **2 hours and 25 minutes** from initial failure to full system recovery. This timeline reflects real-world troubleshooting and resilience under pressure.

- PAM misconfigurations can render all logins invalid — even with correct credentials
- The success message from `passwd` does not always mean the password was applied correctly
- `/etc/pam.d` is a critical authentication stack, and even a minor syntax error in files like `common-auth` or `login` can prevent access
- Using `cat << 'EOF'` is a safe and scriptable way to overwrite broken config files
- Snapshots and config backups are essential parts of OPSEC hygiene

---

## Why It Matters

This experience provided hands-on understanding of:
- Linux authentication systems (PAM, shadow, passwd)
- The importance of operational backups and recovery users
- Real-world troubleshooting and diagnostics under pressure
- How improper system hardening can lead to self-denial of access

This scenario mirrors real-world incidents faced by sysadmins and cybersecurity professionals who must often recover broken production systems under time pressure.

---
    

