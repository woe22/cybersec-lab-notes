# 04 — Banner Grabbing and Enumeration

---

## Scenario

After identifying open services on my target, I needed to go deeper by grabbing banners directly from those services. These banners often reveal useful information like software versions, vendor names, or configuration messages — all of which can inform both attack and defense strategies. The goal was to use manual tools like `telnet`, `nc`, and `curl`, as well as scripted approaches via Nmap, to extract banner data from exposed ports.

---

## What I Did

```bash
# Attempted to grab SSH banner using Telnet
telnet 10.0.2.15 22
```

**Banner Result:**
```
SSH-2.0-OpenSSH_10.0p2 Debian-5
```

```bash
# Tried to grab HTTP headers using curl (port 80)
curl -I http://10.0.2.15
```

**Result:**
```
curl: (7) Failed to connect to 10.0.2.15 port 80: Could not connect to server
```

```bash
# Optional: Nmap banner script scan
sudo nmap -sV --script=banner -oN banner_script.txt 10.0.2.15
```

---

## What I Learned

- Telnet and Netcat can be used to manually connect to TCP services and reveal protocol banners.
- SSH typically returns a version string immediately, making it easy to identify.
- Curl can grab HTTP headers, but only if a service is actually listening on the target port.
- Banner grabbing is a low-noise reconnaissance method that doesn't require full exploitation to gain useful intelligence.
- Service banners can often be matched to known vulnerabilities using databases like CVE or Exploit DB.

---

## Why It Matters

Banner grabbing is a simple but powerful technique for network reconnaissance. It helps defenders identify exposed services and outdated software before attackers do — and it gives red teamers a way to fingerprint systems quickly. Knowing how to extract, interpret, and document banners is essential for threat modeling, vulnerability assessment, and incident response.

---

