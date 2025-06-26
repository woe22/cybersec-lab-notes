# 03 — Networking Tools

---

## Scenario

As a SOC analyst, having hands-on familiarity with core network tools is essential for detecting, investigating, and responding to security events. In this module, I used tools like `nmap`, `tcpdump`, `ss`, and `lsof` to explore how network connections work at the system level. These tools are foundational for both blue team operations and deeper network analysis.

---

## What I Did

- Installed key networking tools:
  ```bash
  sudo apt install net-tools iproute2 nmap tcpdump whois traceroute mtr
  ```

- Explored interfaces and sockets:
  ```bash
  ifconfig         # Legacy interface info
  ip a             # Modern alternative
  netstat -tuln    # Show listening ports
  ss -tuln         # Modern socket status
  ```

- Scanned systems using `nmap`:
  ```bash
  nmap 192.168.1.1
  nmap -sV -O 192.168.1.1
  ```

- Captured traffic with `tcpdump`:
  ```bash
  sudo tcpdump -i any -c 10
  sudo tcpdump -i any -w capture.pcap
  ```

- Investigated DNS with:
  ```bash
  dig google.com
  nslookup github.com
  ```

- Checked live connections and open ports:
  ```bash
  ss -tulnp
  sudo lsof -i -P -n
  sudo lsof -i :22
  ```

- Traced routes and latency:
  ```bash
  traceroute google.com
  mtr google.com
  ```

- Queried domains and IPs using `whois`:
  ```bash
  whois google.com
  whois 1.1.1.1
  ```

---

## What I Learned

- How to view, interpret, and investigate live system ports and connections
- How to scan and identify running services on a network using `nmap`
- How to capture and store raw network traffic with `tcpdump`
- That tools like `ss`, `lsof`, and `netstat` offer different views into system networking
- How DNS resolution, routes, and whois data reveal layers of infrastructure context
- Each tool serves a purpose in threat hunting, triage, or visibility workflows

---

## Why It Matters

In a SOC environment, analysts must often answer questions like:
- Is this port supposed to be open?
- Who owns this suspicious IP?
- Is traffic leaving the network unexpectedly?

These tools form the first line of investigation. They give the analyst visibility and evidence to make informed decisions fast — often under pressure. Mastering them is non-negotiable for real-world incident response.

---

