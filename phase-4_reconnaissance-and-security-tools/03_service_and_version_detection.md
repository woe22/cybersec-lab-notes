# 01 — Service and Version Detection

---

## Scenario

After discovering live hosts on my subnet, I needed to identify which services were running and their exact software versions. Accurate version data allows correlation with known CVEs and helps prioritize remediation or deeper investigation—an everyday task for SOC analysts.

---

## What I Did

```bash
# Identify live hosts
sudo nmap -sn 10.0.2.0/24

# Perform service and version detection on my Kali VM
sudo nmap -sV -oN version_scan.txt 10.0.2.15

# Review saved results
cat version_scan.txt
```

Key output excerpt:
```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 10.0p2 Debian 5 (protocol 2.0)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

---

## What I Learned

- The `-sV` flag tells Nmap to probe service banners and identify software versions.
- Output includes CPE identifiers that map directly to vulnerability databases.
- Saving scans with `-oN` creates a text report useful for ticketing and future diffing.

---

## Why It Matters

Version detection elevates basic port scans into actionable vulnerability intelligence. SOC analysts rely on precise version data to match services against threat feeds and compliance baselines, enabling rapid prioritization of patching efforts.

---

