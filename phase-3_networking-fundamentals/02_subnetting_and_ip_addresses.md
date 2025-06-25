# 02 — Subnetting and IP Addresses

---

## Scenario

To truly understand how networks are structured and protected, I needed to get comfortable with how IP addresses, subnets, and ranges work. This module focused on CIDR notation, private address ranges, and tools like `ipcalc` and `sipcalc` to explore subnet layouts. These concepts are critical when analyzing logs, detecting scans, and writing firewall or detection rules as a SOC analyst.

---

## What I Did

- Explored my system’s IP and subnet info:
  ```bash
  ip a
  ```
- Installed and used `sipcalc` to analyze subnets:
  ```bash
  sudo apt install sipcalc
  sipcalc 192.168.1.0/24
  sipcalc 10.0.0.0/8
  sipcalc 172.16.0.0/12
  ```
- Created a CIDR cheat sheet:
  ```text
  /8    = 255.0.0.0       = 16M hosts
  /16   = 255.255.0.0     = 65K hosts
  /24   = 255.255.255.0   = 254 hosts
  /30   = 255.255.255.252 = 2 hosts
  ```
- Installed and used `ipcalc`:
  ```bash
  sudo apt install ipcalc
  ipcalc 192.168.10.0/24
  ipcalc 192.168.1.128/25
  ```
- Understood reserved IP ranges:
  ```text
  Private:
  - 10.0.0.0/8
  - 172.16.0.0/12
  - 192.168.0.0/16

  Loopback: 127.0.0.0/8
  Link-local: 169.254.0.0/16
  ```
- Practiced subnetting logic and VLSM examples with `/25` splits.

---

## What I Learned

- CIDR notation determines how many IPs are available and which addresses are reserved
- Subnets can be used to logically segment networks and limit access
- Tools like `ipcalc` and `sipcalc` make subnet planning and log interpretation much easier
- Knowing the range and structure of subnets helps detect recon behavior (e.g., ping sweeps)
- Wildcard masks are used in access control and firewall rules

---

## Why It Matters

Being able to interpret IP ranges and subnet boundaries is critical for any cybersecurity role, especially in log analysis and alert triage. Whether defending against lateral movement, analyzing firewall logs, or whitelisting known networks, subnetting fundamentals enable SOC analysts to respond more effectively and with greater context.

---

