# 02 — Networking Essentials

---

## Scenario

This module focused on establishing a foundational understanding of Linux networking essentials. As a SOC analyst working in a lab or production environment, diagnosing network issues, resolving DNS failures, and understanding routing and connectivity are essential. This lab included hands-on commands to inspect IP addressing, gateways, DNS resolution, local ports, and interface status — all directly relevant to troubleshooting and monitoring.

---

## What I Did

- Viewed all IP interfaces and routing tables:
  ```bash
  ip a
  ip r
  hostname -I
  ```
- Inspected current DNS resolver configuration:
  ```bash
  cat /etc/resolv.conf
  ```
- Diagnosed and resolved a broken DNS setup:
  - Discovered `nameserver 127.0.0.1` was failing
  - Attempted to overwrite `/etc/resolv.conf` and encountered permission errors
  - Unlocked file with:
    ```bash
    sudo chattr -i /etc/resolv.conf
    ```
  - Replaced file using:
    ```bash
    echo -e "nameserver 1.1.1.1\nnameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null
    ```
- Verified DNS was working using:
  ```bash
  ping -c 4 google.com
  ```
- Examined routing table and default gateway:
  ```bash
  ip route show
  ```
- Explored `/etc/hosts` and learned how local host overrides work
- Identified open network ports and services:
  ```bash
  sudo ss -tuln
  ```
- Listed network interfaces and status:
  ```bash
  ip link show
  ```

---

## What I Learned

- How to inspect and interpret Linux IP configurations and routing tables
- That DNS resolution depends on `/etc/resolv.conf`, and how resolvers like `systemd-resolved` or misconfigured files can break name resolution
- The role of `127.0.0.1` and how relying on a non-functioning local resolver can silently break internet access
- How to override and secure resolver settings using `tee` and `chattr` in restricted environments
- How to verify basic connectivity via `ping`, diagnose with `traceroute`, and confirm open ports via `ss`
- The difference between direct IP testing and full DNS-based connectivity checks

---

## Why It Matters

Networking is the lifeblood of cybersecurity operations. From detecting anomalous traffic to configuring sensors or validating firewall behavior, SOC analysts must be fluent in interpreting and troubleshooting network behavior. This module hardened my confidence in diagnosing DNS and interface issues — essential skills for real-time alert validation and system triage in a professional security environment.

---

