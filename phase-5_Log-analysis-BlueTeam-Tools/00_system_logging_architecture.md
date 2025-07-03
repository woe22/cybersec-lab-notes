# 00 — Prelude: System Logging + Architecture

---

## Scenario

Before diving into deep log analysis, I needed to understand how my Linux system actually stores and manages logs. This meant investigating the logging architecture, learning where logs are kept, and identifying which services are responsible for writing them. Since my system doesn’t use rsyslog, this module focused on systemd-journald and the `journalctl` command.

---

## What I Did

```bash
# Listed contents of the traditional log directory
ls -lh /var/log

# Checked for rsyslog presence
ps aux | grep rsyslog
systemctl status rsyslog
# → rsyslog not found

# Explored journal logs
journalctl --no-pager | head -n 20

# Followed logs in real time
sudo journalctl -f

# Simulated log events
sudo su
exit

# Checked boot logs
journalctl -b | head -n 30
```

---

## What I Learned

- My system uses **systemd-journald**, not rsyslog, meaning logs are stored in binary format and accessed via `journalctl`.
- The `journalctl -f` command provides a real-time stream of log events, similar to `tail -f`.
- Boot-time logs can be viewed with `journalctl -b`, showing kernel and initialization messages.
- Common services like `CRON`, `sudo`, and Xfce tools log to the journal and can be traced back to specific user sessions.

---

## Why It Matters

Understanding how logs are captured, stored, and accessed is a core responsibility for any SOC analyst. Whether troubleshooting a failed login or tracking suspicious behavior, knowing where logs live and how to extract relevant entries is foundational to detection and response. This module laid the groundwork for filtering, investigating, and correlating logs across the system — skills I’ll build on in future modules.

---
