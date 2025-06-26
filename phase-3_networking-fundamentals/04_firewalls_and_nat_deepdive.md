# 04_firewall_and_nat_advanced.md

---

## Scenario

After learning basic firewall management in Phase 1, it's time to level up. In this module, I explored advanced firewall rules using both `nftables` and `iptables`, configured NAT redirection, and tested web service accessibility and packet filtering. This step is crucial for understanding how modern Linux systems control traffic in and out of networks, a core skill for any SOC analyst.

---

## What I Did

```bash
# List nftables tables
sudo nft list tables

# Check iptables NAT rules
sudo iptables -t nat -L -n -v

# Redirect incoming traffic on port 8080 to port 80
sudo iptables -t nat -A PREROUTING -p tcp --dport 8080 -j REDIRECT --to-port 80

# Test Apache accessibility
curl http://localhost:8080

# Install and start Apache
sudo apt install apache2 -y
sudo systemctl start apache2
sudo systemctl status apache2

# View if Apache is listening on port 80
sudo ss -tuln | grep :80

# Test DNS resolution
curl https://google.com

# Allow outbound traffic on port 443 (HTTPS) using UFW
sudo ufw allow out to any port 443 proto tcp

# Check and fix DNS settings
ls -l /etc/resolv.conf
echo -e "nameserver 1.1.1.1\nnameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null

# Restart networking
sudo systemctl restart networking

# Test internet connectivity
ping -c 3 1.1.1.1
curl https://google.com
```

---

## What I Learned

- The difference between `nftables` and `iptables`, and how both can coexist in modern Linux systems.
- How to set up NAT redirection with `iptables` and verify it with `curl`.
- Apache must be started and listening on port 80 for redirection to succeed.
- Proper DNS configuration is critical for resolving domain names.
- Promiscuous mode is unsupported on some interfaces like `any`, affecting tools like `tcpdump`.
- UFW can manage specific outbound traffic rules like HTTPS.

---

## Why It Matters

Understanding NAT and firewall redirection deepens my control over traffic flows and strengthens my ability to troubleshoot complex network issues. These are critical skills for incident response and threat detection in SOC environments. Mastery here prepares me for handling real-world traffic visibility and filtering scenarios with confidence.


---
