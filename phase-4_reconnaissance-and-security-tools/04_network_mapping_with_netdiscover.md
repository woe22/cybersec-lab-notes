# 04 - Network Mapping With Netdiscover

---

## Scenario

In this module, I needed to identify active hosts within my local subnet without sending aggressive traffic or relying on high-profile tools. The objective was to perform passive or semi-passive reconnaissance using `netdiscover` to map out devices on my local network and understand basic ARP-level host discovery.

---

## What I Did

```bash
# Verified my network configuration and IP/subnet
ip route

# Observed my subnet as 10.0.2.0/24

# Ran netdiscover in active scan mode
sudo netdiscover -r 10.0.2.0/24

# Saved the output to a log file
sudo netdiscover -r 10.0.2.0/24 > netdiscover_results.txt

# Reviewed the results
cat netdiscover_results.txt
```

**netdiscover_results.txt Output:**
```
2 Captured ARP Req/Rep packets, from 2 hosts.   Total size: 128
-------------------------------------------------------------------
IP             MAC Address         Count  Len  MAC Vendor / Hostname
10.0.2.2       52:55:0a:00:02:02     1     64   Unknown vendor
10.0.2.3       52:55:0a:00:02:03     1     64   Unknown vendor
```

---

## What I Learned

- `netdiscover` uses ARP to identify live hosts on a local subnet.
- Even in NAT-mode VMs, it's possible to detect other virtualized network components like internal gateways or companion VMs.
- MAC addresses can offer insight into hardware manufacturers (though in this case, they returned as unknown vendors).
- Passive scanning (`-p`) doesn't generate traffic but relies on sniffing ARP broadcasts, while specifying a range (`-r`) is an active approach.

---

## Why It Matters

Understanding local network topology is foundational for any blue team or red team activity. This kind of low-noise scanning can help identify unauthorized devices or verify network segmentation. Practicing with ARP-level discovery reinforces knowledge of basic network communication and how adversaries might silently enumerate hosts during internal reconnaissance.

---

