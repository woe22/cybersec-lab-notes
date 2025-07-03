# 01 — Log File Navigation & Filtering

---

## Scenario

As a SOC analyst, I need to be able to navigate massive log files quickly and extract actionable insights. This module focused on using command-line tools like `less`, `grep`, `awk`, and `cut` to work with exported log data. Even though my logs didn't contain failed login attempts, I still gained experience with key filtering and search commands.

---

## What I Did

```bash
# Exported 100 SSH-related log entries from the journal
journalctl -u ssh.service --since "1 day ago" -n 100 > authlog_sample.txt

# Searched for login failures
grep "Failed password" authlog_sample.txt

# Exported a wider date range to look for more entries
journalctl -u ssh.service --since "7 days ago" > authlog_sample.txt
grep "Failed password" authlog_sample.txt

# Opened the log file in less for manual inspection
less authlog_sample.txt

# Practiced extracting data using pipes
grep "Failed password" authlog_sample.txt | awk '{print $(NF-3)}' | sort | uniq -c | sort -nr
```

---

## What I Learned

- `journalctl` can export logs into plaintext for offline analysis.
- `grep` is useful for quickly searching for terms like “Failed password” or “sudo”.
- `less` makes it easy to scroll, search, and navigate large files interactively.
- Pipes allow for powerful one-liner filters and summaries by combining commands like `grep`, `awk`, `sort`, and `uniq`.
- Even with clean logs, the process of filtering, navigating, and extracting data is valuable for incident response readiness.

---

## Why It Matters

SOC analysts often work under pressure — whether responding to alerts or digging through logs during an incident. Mastering these tools ensures I can filter the signal from the noise efficiently. Even in quiet systems, the ability to search and verify that nothing suspicious occurred is just as critical as finding malicious activity.

---

