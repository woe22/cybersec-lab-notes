# 04 — Introduction to SIEM Concepts

---

## Scenario

As a future SOC analyst, I need to understand how SIEM (Security Information and Event Management) systems function and how they support detection, investigation, and response workflows. In this module, I simulated core SIEM logic using local Linux tools and researched real-world SIEM platforms to bridge the conceptual gap between manual log analysis and enterprise-grade monitoring.

---

## What I Did

```bash
# Simulated a brute-force alert rule
journalctl -u ssh.service --since "24 hours ago" | grep "Failed password" | awk '{print $(NF-3)}' | sort | uniq -c | sort -nr

# Classified alert severities based on log message types

# Browsed and reviewed SIEM platforms:
# - Wazuh (open source)
# - Splunk (enterprise)
# - Microsoft Sentinel (cloud-native)
```

---

## What I Learned

- A SIEM platform ingests logs from across an environment, normalizes and correlates them, and then raises alerts when certain patterns match detection rules.
- Local log tools like `journalctl`, `grep`, and `awk` can simulate basic SIEM correlation logic — such as identifying repeated failed login attempts.
- Severity classification is key in a SOC workflow — not all alerts require the same level of response.
- Open source SIEMs (like Wazuh) offer great entry points for blue teamers, while enterprise tools like Splunk and Sentinel offer more scale and automation.

---

## Why It Matters

SIEMs are central to modern blue team operations. They act as the brain of the SOC, turning raw log data into actionable alerts. Knowing how they work — and how to mimic their behavior manually — builds the foundations for working in a SOC environment, writing detection rules, and responding to real-world incidents with clarity and speed.

---


