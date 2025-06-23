# 04 — Tor and DNS Privacy

## Scenario
To enhance anonymity and prevent DNS leakage, I configured my Kali Linux virtual machine to use Tor for web traffic and dnscrypt-proxy to encrypt and anonymize DNS queries. This ensures that both browsing activity and DNS requests are protected from surveillance and tracking.

## What I Did
- Installed and configured `dnscrypt-proxy` to route DNS queries securely.
- Edited `/etc/dnscrypt-proxy/dnscrypt-proxy.toml`:
  - Set `listen_addresses = ['127.0.0.1:53']`
  - Enabled `require_dnssec = true` to enforce DNSSEC
  - Set `ipv6_servers = false` to disable IPv6 leakage
  - Enabled logging under `[query_log]` to `/var/log/dnscrypt-proxy/query.log`
- Changed my system resolver:
  - Unlocked `/etc/resolv.conf` with `sudo chattr -i`
  - Set nameserver to `127.0.0.1`
  - Relocked with `sudo chattr +i`
- Verified that `dnscrypt-proxy` was listening on `127.0.0.1:53` via:
  ```bash
  sudo ss -tuln | grep :53
  ```
- Tested DNS resolution through DNSCrypt:
  ```bash
  dig github.com @127.0.0.1
  ```
- Verified query logs:
  ```bash
  sudo tail -f /var/log/dnscrypt-proxy/query.log
  ```
- Observed successful query logging from `127.0.0.1` using the Cloudflare resolver.

## What I Learned
- **Tor** anonymizes traffic by routing it through multiple encrypted relays.
- **dnscrypt-proxy** encrypts DNS queries and supports secure resolvers with DNSSEC validation.
- Listening on `127.0.0.1:53` ensures local-only DNS routing, avoiding leaks.
- DNSSEC ensures that DNS responses haven’t been tampered with.
- Immutable `/etc/resolv.conf` prevents unintended overwriting by NetworkManager or system updates.

## Why It Matters
DNS is one of the most commonly leaked sources of metadata. Even with Tor enabled, if DNS is not secured, ISPs or adversaries can still observe what domains you access. By combining `dnscrypt-proxy` with local DNS resolution and Tor for HTTP/S traffic, we achieve layered privacy protection—critical for secure environments, OSINT, or red teaming operations.

---


