# 05 — VPN and Proxy Config

---

## Scenario

Secure traffic routing and anonymity are vital for analysts who investigate malicious infrastructure or access sensitive resources from untrusted networks. In this module I configured a system‑wide VPN (ProtonVPN CLI) and a local proxy chain (Tor + Proxychains) on Kali Linux, verified IP/DNS leak protection, and learned the limitations of vendor‑specific VPNs such as Brave VPN.

---

## What I Did

```bash
# 1. Installed required packages
sudo apt update
sudo apt install -y openvpn wireguard python3-pip pipx proxychains4 tor

# 2. Installed ProtonVPN CLI safely with pipx
pipx install protonvpn-cli
sudo protonvpn init                 # provided credentials & default UDP config
sudo protonvpn connect --fastest    # established VPN tunnel

# 3. Verified new public IP
curl ifconfig.me

# 4. Checked DNS leak status
proxychains curl https://dnsleaktest.com/plain

# 5. Configured Proxychains to use local Tor SOCKS5
sudo sed -i '$a socks5  127.0.0.1 9050' /etc/proxychains.conf
sudo systemctl start tor
proxychains curl ifconfig.me        # IP different from direct VPN

# 6. Explored Brave VPN limitations (browser‑only, no Linux CLI)
echo "Brave VPN is not usable for system‑wide CLI routing—documented in notes."

# 7. Hardened DNS: manual override
echo -e "nameserver 1.1.1.1\nnameserver 8.8.8.8" | sudo tee /etc/resolv.conf
sudo chattr +i /etc/resolv.conf     # prevent overwrite

# 8. Logged all outputs and screenshots for GitHub doc
```

---

## What I Learned

- **pipx** is the Kali‑approved method for installing Python CLI tools without breaking system packages.
- ProtonVPN provides free, reputable servers and WireGuard/OpenVPN configs suitable for lab use.
- **Tor over VPN via Proxychains** adds an additional anonymity layer and allows selective proxying of tools.
- DNS leaks can expose real location even if VPN is up; manual `/etc/resolv.conf` hardening plus VPN DNS prevents leaks.
- Brave VPN is restricted to its GUI context and cannot be leveraged for system‑wide tunnels on Linux.
- Combining firewall knowledge with VPN/proxy chains prepares me for blue‑team and red‑team traffic routing scenarios.

---

## Why It Matters

Real‑world SOC analysts must safely pivot through VPNs or proxies when researching malicious domains, accessing isolated environments, or protecting their infrastructure. Mastering VPN CLI setup, DNS hygiene, and proxy chaining equips me to avoid attribution, reduce detection risk, and validate secure network egress paths during investigations.

---

