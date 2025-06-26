# 01 — Nmap and Scanning

---

## Scenario

To transition from network fundamentals to active reconnaissance, I needed a reliable way to discover hosts, enumerate services, and gather preliminary vulnerability data. This module focused on mastering **Nmap**—the industry‑standard port scanner—and applying multiple scan types against my local lab subnet. The hands‑on work mirrors the discovery stage in both penetration testing and blue‑team asset inventory.

---

## What I Did

- Identified my network details:
  ```bash
  ip a | grep inet          # Found local IP 10.0.2.15/24
  ip route | grep default   # Gateway 10.0.2.2
  ```
- Performed a **ping sweep** of the subnet:
  ```bash
  sudo nmap -sn 10.0.2.0/24
  ```
- Ran a **stealth SYN scan** against the gateway:
  ```bash
  sudo nmap -sS 10.0.2.2
  ```
- Collected **service versions** and **OS detection** data:
  ```bash
  sudo nmap -sV -O 10.0.2.2
  ```
- Executed a **full TCP port scan** to reveal less‑common services:
  ```bash
  sudo nmap -p- 10.0.2.2
  ```
- Saved results to files for later analysis:
  ```bash
  nmap -sV -oN basic_scan.txt 10.0.2.2
  nmap -A   -oX full_scan.xml 10.0.2.2
  ```
- Explored the **Nmap Scripting Engine** for quick vuln checks:
  ```bash
  sudo nmap --script vuln 10.0.2.2
  ```

---

## What I Learned

- The difference between **ping sweeps** (`-sn`) and **port scans** (`-sS`, `-sV`).
- How CIDR notation (`/24`) defines the subnet range for discovery.
- **SYN scans** are stealthier than full TCP connects and often bypass basic firewalls.
- `-sV` and `-O` reveal detailed banner and OS information valuable for vulnerability matching.
- The **NSE** (`--script`) can perform quick vulnerability checks without separate tools.
- Always store scan outputs (`-oN`, `-oX`) for evidence, diffing, or report inclusion.

---

## Why It Matters

Effective reconnaissance is the first step of every penetration test and the backbone of asset visibility for blue teams. Mastering Nmap enables me to rapidly:

- Inventory live hosts and exposed services.
- Identify potential weak points before attackers do.
- Validate firewall effectiveness and segmentation.
- Collect structured data for subsequent vulnerability scanning.

These skills directly translate to day‑one SOC tasks such as alert enrichment, baseline assessments, and threat hunting.

---

