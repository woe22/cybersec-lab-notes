# 03 — Log Rotation and Persistence

---

## Scenario

Logs can grow uncontrollably if not properly rotated or cleaned. As a future SOC analyst, I need to understand how Linux manages log size, retention, and system persistence to ensure forensic data isn’t lost and disk space isn’t exhausted. This module focused on exploring `logrotate`, checking default policies, and ensuring journald logs persist across reboots.

---

## What I Did

```bash
# Checked if logrotate was installed
which logrotate
logrotate --version

# Inspected global logrotate configuration
cat /etc/logrotate.conf

# Listed and reviewed application-specific rotation rules
ls /etc/logrotate.d/
cat /etc/logrotate.d/rsyslog

# Forced a manual log rotation
sudo logrotate -f /etc/logrotate.conf

# Checked for compressed rotated logs
ls -lh /var/log | grep '\.gz'

# Verified if journald logs persist across reboots
ls -lh /var/log/journal

# (If needed) Enabled journal persistence
sudo mkdir -p /var/log/journal
sudo systemd-tmpfiles --create --prefix /var/log/journal
sudo systemctl restart systemd-journald
```

---

## What I Learned

- `logrotate` is the traditional utility for managing plaintext logs in `/var/log`.
- The main configuration file is `/etc/logrotate.conf`, which includes app-specific rules from `/etc/logrotate.d/`.
- Log files are often compressed as `.gz` during rotation to save space.
- `systemd-journald` by default stores logs in memory unless a persistent journal directory is created.
- Persistent logging is important for maintaining evidence across reboots or crashes.

---

## Why It Matters

Without log rotation, systems risk running out of disk space — potentially crashing critical services. Without persistence, logs can be lost between reboots, which is disastrous during forensic investigations or long-term monitoring. As a SOC analyst, ensuring log reliability, longevity, and searchability is a foundational skill that protects uptime and enables accountability.

---

