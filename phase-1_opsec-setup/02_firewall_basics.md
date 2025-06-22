    # 02 — Firewall Basics

## Scenario
In this module, the objective was to understand and implement basic host-based firewall rules using UFW (Uncomplicated Firewall). This is crucial for protecting the system from unauthorized inbound connections while allowing secure outbound traffic.

## What I Did
- Ensured UFW was installed on the Kali Linux VM:
  ```bash
  sudo apt install ufw
  ```
- Configured default firewall rules to deny all incoming and allow all outgoing traffic:
  ```bash
  sudo ufw default deny incoming
  sudo ufw default allow outgoing
  ```
- Allowed SSH access to retain remote or local login capability:
  ```bash
  sudo ufw allow ssh
  ```
- Enabled the firewall:
  ```bash
  sudo ufw enable
  ```
- Verified firewall rules with:
  ```bash
  sudo ufw status verbose
  ```
- Attempted a port scan using Nmap:
  ```bash
  nmap -Pn <kali-ip>
  ```
- Found that additional ports were showing or SSH was not detected. Troubleshot with:
  ```bash
  sudo ss -tuln
  sudo ss -tuln | grep :22
  ```
- Discovered SSH daemon was not actively running despite being installed:
  ```bash
  which sshd
  sudo systemctl status ssh
  ```
- Started and enabled SSH service:
  ```bash
  sudo systemctl enable ssh
  sudo systemctl start ssh
  ```
- Re-ran checks and confirmed SSH was listening:
  ```bash
  sudo ss -tuln | grep :22
  ```
- Re-ran Nmap and confirmed only port 22 was open.

## What I Learned
- UFW allows for quick rule setup, but it’s only effective if the services it’s intended to protect are running properly.
- `ss -tuln` is a useful command to see what services are actively listening on the system.
- `nmap -Pn` allows scanning of ports even if ICMP/ping is blocked — a good test for real-world scenarios.
- It's important to align actual running services (`systemctl status`) with firewall rules (`ufw allow`).

## Why It Matters
Being able to troubleshoot firewall and service mismatches is critical in real-world scenarios where port exposure can result in system compromise. This exercise reinforced how firewall rules, service status, and network exposure all interconnect. Mastering these tools allows a practitioner to confidently lock down systems and verify their security posture.

  
