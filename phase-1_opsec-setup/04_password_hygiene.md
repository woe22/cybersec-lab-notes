# 03_password_hygiene.md

**Date Completed:** 2025-06-22

## Scenario

This module focuses on understanding and applying password hygiene best practices in a secure Linux environment. As part of OPSEC hygiene, enforcing strong password policies, managing expiration, and protecting against reuse are critical first steps to hardening any user-based system. This lab emphasizes how user credentials are managed at the system level in Kali Linux.

## What I Did

- Explored password storage:
  ```bash
  cat /etc/passwd
  sudo cat /etc/shadow
  ```
- Changed the current user's password:
  ```bash
  passwd
  ```
- Created a new test user:
  ```bash
  sudo adduser securetest
  sudo passwd securetest
  ```
- Set a password policy with `chage`:
  ```bash
  sudo chage -M 90 -m 7 -W 14 <username>
  sudo chage -l <username>
  ```
- Edited PAM settings to prevent password reuse:
  ```bash
  sudo nano /etc/pam.d/common-password
  ```
  Ensured the following lines were present:
  ```
  password requisite pam_pwquality.so retry=3
  password required pam_pwhistory.so use_authtok remember=5
  ```
- Configured account lockout policy with `faillock.conf`:
  ```bash
  sudo nano /etc/security/faillock.conf
  ```
  Set:
  ```
  deny = 3
  unlock_time = 600
  ```

## What I Learned

- Linux separates user info (`/etc/passwd`) from password hashes (`/etc/shadow`) to protect credential integrity.
- The `passwd` command changes user passwords securely.
- `chage` helps enforce aging and warning policies to require password updates over time.
- PAM modules like `pam_pwquality.so` and `pam_pwhistory.so` enforce strong password complexity and prevent reuse.
- `faillock.conf` protects accounts by locking users out after repeated login failures, reducing brute-force risks.

## Why It Matters

Weak passwords are a major vector for system compromise. Enforcing good password hygiene protects against brute-force, dictionary, and credential reuse attacks. Learning how to configure system-wide password policies is an essential skill for security professionals, especially in environments where user access control is critical.

---
