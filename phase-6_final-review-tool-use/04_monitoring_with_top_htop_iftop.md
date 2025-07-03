# 04 — Monitoring with `top`, `htop`, `iftop`

---

## Scenario

This module focused on real-time system and network monitoring using interactive tools. These skills are essential for SOC analysts or incident responders who need to quickly assess live system health, detect spikes in resource usage, and identify potentially malicious connections on the fly.

---

## What I Did

```bash
# Monitored active processes and system performance
top
# Used Shift + P and Shift + M to sort by CPU and memory

# Installed and used htop for improved process visibility
sudo apt install htop
htop
# Used search, tree view, and filtering to spot suspicious processes

# Installed and used iftop to monitor network traffic
sudo apt install iftop
sudo iftop -i <network_interface>
# Found my interface using:
ip a

# (Bonus) Checked disk and directory usage
df -h
du -sh /var
```

---

## What I Learned

- `top` and `htop` provide fast insight into system load and active processes, and help detect abnormal CPU/memory usage.
- `htop` makes it easier to visualize parent/child process relationships, which is useful for spotting hidden backdoors or forks.
- `iftop` provides a live view of network activity — useful for identifying unauthorized connections or data exfiltration.
- Understanding resource baselines helps detect deviations that might indicate compromise.

---

## Why It Matters

The ability to analyze a system live — without needing logs or delay — is powerful during an active investigation. These tools help SOC analysts determine whether an alert is credible, which process is responsible, and how widespread an issue might be. Mastery of system and network monitoring is key for real-time detection and containment.

---
