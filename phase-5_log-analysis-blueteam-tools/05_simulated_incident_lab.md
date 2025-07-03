# 05 — Mini SOC Lab: Simulated Incident Review

---

## Scenario

In this capstone module, I acted as a Tier 1 SOC analyst responding to a suspicious authentication log containing signs of brute-force attempts and potential compromise. I analyzed a provided log file (`incident_authlog.txt`) to determine what happened, identify the attacker, and assess whether privileged actions were taken.

---

## What I Did

```bash
# Created a simulated log file
cat incident_authlog.txt

# Identified brute-force attempts
grep "Failed password" incident_authlog.txt | awk '{print $(NF-3)}' | sort | uniq -c | sort -nr

# Checked for successful logins
grep "Accepted password" incident_authlog.txt

# Investigated privilege escalation attempts
grep "sudo" incident_authlog.txt
```

---

## What I Learned

- Brute-force attempts often precede a successful login — patterns of failed attempts followed by acceptance are suspicious.
- The IP `192.168.1.22` was involved in both failed and successful logins.
- A successful root login occurred, and shortly after, a privileged action was executed using `sudo` to launch a root shell.
- Privileged actions can be identified in logs by searching for the `sudo` keyword or direct root shell activity.

---

## Findings Summary

| Field                     | Result              |
|---------------------------|---------------------|
| IP Address Involved       | 192.168.1.22        |
| Failed Login Attempts     | 2                   |
| Successful Login?         | ✅ Yes              |
| Privileged Action Taken?  | ✅ Yes — `/bin/bash` via `sudo` |

---

## Why It Matters

This simulation reinforced my ability to rapidly investigate authentication logs and identify the difference between routine noise and serious security incidents. Understanding log patterns, correlating failed logins with privilege escalation, and summarizing findings clearly is a key skill for any SOC analyst.

---
