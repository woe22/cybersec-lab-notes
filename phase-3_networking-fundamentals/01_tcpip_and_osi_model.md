# 01 — TCP/IP and the OSI Model

---

## Scenario

Before diving into network security tools, I needed to understand how systems communicate at the protocol level. This module focused on understanding the OSI model, TCP/IP architecture, and the tools used to analyze live network traffic and connections. Building this foundation is essential to interpreting data in packet captures, log files, and threat intelligence feeds as a SOC analyst.

---

## What I Did

- Created a file listing the 7 layers of the OSI model:
  ```bash
  cat << 'EOF' > osi_layers.txt
  7 - Application
  6 - Presentation
  5 - Session
  4 - Transport
  3 - Network
  2 - Data Link
  1 - Physical
  EOF
  ```
- Mapped real-world protocols to OSI layers:
  ```
  Application: HTTP, HTTPS, DNS, FTP, SSH
  Transport: TCP, UDP
  Network: IP, ICMP
  Data Link: Ethernet, ARP
  Physical: Cables, Wi-Fi signals
  ```
- Used network interface tools:
  ```bash
  ip a
  ifconfig
  ```
- Inspected listening ports and services:
  ```bash
  ss -tuln
  netstat -tuln
  ```
- Tested connectivity and routing paths:
  ```bash
  ping -c 1 1.1.1.1
  traceroute google.com
  ```
- Captured live packet traffic with:
  ```bash
  sudo tcpdump -i any -c 10
  ```
- Compared the OSI and TCP/IP models in a file:
  ```
  OSI:      7-App 6-Pres 5-Sess 4-Trans 3-Net 2-DataLink 1-Physical
  TCP/IP:   App       Trans     Net       Link
  ```

---

## What I Learned

- The OSI model provides a conceptual framework for how network communications work, layer by layer
- TCP/IP is a simpler, practical model used by the internet and Linux systems
- Commands like `ip a`, `ss`, `ping`, and `tcpdump` provide critical insights into network activity
- The `any` device in `tcpdump` aggregates interfaces but cannot enter promiscuous mode
- Mapping protocols to layers helps interpret logs, firewalls, and packet captures during analysis

---

## Why It Matters

Understanding TCP/IP and the OSI model is foundational for any cybersecurity role. Whether analyzing logs, working in a SIEM, performing packet captures, or configuring firewall rules, this conceptual grounding allows analysts to interpret where and how network issues or attacks are occurring. This knowledge is directly tied to real-world tasks like detecting lateral movement, investigating suspicious traffic, and setting alerts for unusual protocol usage.

---

