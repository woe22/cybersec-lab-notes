# 02 — Syslog, rsyslog, and Journalctl

---

## Scenario

In this module, I explored the Linux logging infrastructure — specifically the differences between traditional `rsyslog`-based systems and modern `systemd-journald`. My Kali Linux environment does not use `rsyslog`, so I focused on `journalctl`, how logs are handled in binary format, and how to simulate log entries using `logger`.

---

## What I Did

```bash
# Confirmed rsyslog is not installed
systemctl status rsyslog

# Used logger to generate a custom log entry
logger "🔥 TEST: custom log entry from user woe"

# Viewed the entry using journalctl
journalctl -t woe --since "5 minutes ago"

# Viewed systemd journal configuration
cat /etc/systemd/journald.conf | grep -v "^#"

# Listed boot sessions recorded in the journal
journalctl --list-boots
```

---

## What I Learned

- My system uses `systemd-journald` for all logging, which stores logs in a binary journal format rather than plaintext.
- The `logger` command is a simple way to generate test log entries, useful for alert testing or tool validation.
- `journalctl` is the primary tool for querying logs under systemd, supporting time-based filtering, service filters, and tags.
- The default journald configuration is sufficient for local logging but can be customized for persistence, forwarding, or log retention.

---

## Why It Matters

Understanding how Linux handles logs at the system level is critical for a SOC analyst. Being able to simulate, search, and configure logs allows analysts to verify events, troubleshoot incidents, and ensure logging coverage is complete. This knowledge also bridges the gap between legacy syslog pipelines and modern systemd-based environments.

---

