# 07 — Log Exploration Basics

---

## Scenario

This module focused on developing a foundational understanding of how Linux logs work in a modern systemd-based environment. Unlike traditional systems that use flat log files like `/var/log/syslog`, Kali Linux uses `systemd-journald` as its primary logging mechanism. I explored how logs are stored, viewed, filtered, and monitored using `journalctl` — a core skill for triaging events and investigating suspicious activity in a SOC workflow.

---

## What I Did

- Navigated to the `/var/log` directory and explored its contents:
  ```zsh
  cd /var/log
  ls -lh
  ```
- Confirmed that `syslog` is not present due to `systemd-journald` being used
- Viewed live logs using:
  ```zsh
  journalctl -f
  ```
- Inspected recent and critical events:
  ```zsh
  journalctl -xe
  ```
- Searched logs for specific keywords and failed actions:
  ```zsh
  journalctl | grep sudo
  journalctl | grep -i failed
  ```
- Filtered logs by specific system services:
  ```zsh
  journalctl -u ssh
  ```
- Queried logs based on time windows:
  ```zsh
  journalctl --since "1 hour ago"
  journalctl --since today
  ```
- Viewed boot-level kernel logs:
  ```zsh
  dmesg | less
  ```
- Investigated log rotation settings:
  ```zsh
  cat /etc/logrotate.conf
  ls /etc/logrotate.d/
  ```

---

## What I Learned

- Modern Linux systems like Kali use `systemd-journald`, which stores logs in a binary format accessed via `journalctl`
- Traditional files like `/var/log/syslog` do not exist unless `rsyslog` is explicitly enabled
- `journalctl` supports powerful filters by time, service, priority, and keywords
- Real-time log monitoring (`journalctl -f`) is essential for debugging active issues
- Log rotation is still used for certain flat-file logs and is configured via `logrotate.conf`
- Understanding the logging system is foundational to alert validation, incident response, and system hardening

---

## Why It Matters

Logs are often the first source of truth when diagnosing issues or investigating security events. The ability to confidently read, filter, and understand log output is critical for SOC analysts. This module deepened my comfort with log inspection in modern Linux systems and laid the groundwork for future modules on log analysis and SIEM integration.

---

