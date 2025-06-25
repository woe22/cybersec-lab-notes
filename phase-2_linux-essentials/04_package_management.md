# 04 — Process & Service Monitoring

---

## Scenario

In this module, I explored how to inspect, manage, and control system processes and services in a Linux environment using command-line tools. These skills are critical for any SOC analyst or system administrator monitoring system health, identifying rogue processes, or investigating performance issues. I learned how to track resource usage, identify service status, and control process behavior in real time.

---

## What I Did

- Viewed all running processes:
  ```zsh
  ps aux | less
  ```
- Sorted processes by memory and CPU usage:
  ```zsh
  ps aux --sort=-%mem | head -n 10
  ps aux --sort=-%cpu | head -n 10
  ```
- Used real-time monitoring tools:
  ```zsh
  top
  sudo apt update && sudo apt install htop
  htop
  ```
- Located process IDs for specific services:
  ```zsh
  pgrep ssh
  pidof systemd
  ```
- Attempted to kill a root-owned SSH process:
  ```zsh
  kill 880            # Permission denied
  sudo kill 880       # Successful with sudo
  sudo pkill ssh      # Killed all SSH-related processes
  ```
- Restarted the SSH service:
  ```zsh
  sudo systemctl restart ssh
  ```
- Explored active and enabled services:
  ```zsh
  systemctl list-units --type=service
  systemctl status ssh
  sudo systemctl enable ssh
  ```
- Investigated autostart configurations:
  ```zsh
  ls /etc/systemd/system/
  ls ~/.config/autostart/     # Directory did not exist
  ```

---

## What I Learned

- `ps`, `top`, and `htop` provide different views into system process behavior
- Sorting by memory and CPU usage is useful for detecting resource hogs
- Root-owned processes require privilege escalation (`sudo`) to manage
- `pgrep`, `pidof`, `kill`, and `pkill` are precise tools for process targeting
- `systemctl` is the central interface for managing services in systemd
- Autostart services can be found globally under `/etc/systemd/system/` or per-user in `~/.config/autostart/`
- Understanding process management is essential for monitoring system integrity and identifying malicious or abnormal behavior

---

## Why It Matters

Processes and services are where malicious code often lives. Being able to identify, inspect, and control these elements is a foundational defensive skill. This module taught me how to investigate what's running on a system, isolate suspicious behavior, and take control — all without relying on a GUI. These are core capabilities for SOC triage, threat hunting, and host-based response.

---

