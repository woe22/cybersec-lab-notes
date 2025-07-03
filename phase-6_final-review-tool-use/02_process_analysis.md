# 02 — Process Analysis with `ps`, `lsof`, etc

---

## Scenario

In this module, I practiced live endpoint inspection techniques using built-in Linux tools. These commands allow a SOC analyst or incident responder to detect suspicious processes, open network connections, and rogue binaries without relying on GUI tools or external EDR platforms. The goal was to simulate real-world triage on a potentially compromised machine.

---

## What I Did

```bash
# Checked top CPU-consuming processes
ps aux --sort=-%cpu | head

# Inspected established network connections
sudo lsof -i -n -P | grep ESTABLISHED

# Viewed listening ports
sudo netstat -tulnp 2>/dev/null | grep LISTEN
# or
ss -tulnp

# Traced open files by process ID
sudo lsof -p <PID>

# Searched for suspicious binaries in nonstandard locations
ps aux | grep '/tmp/'
```

---

## What I Learned

- Processes consuming excessive CPU or running from nonstandard directories (e.g., `/tmp/`, `/dev/shm/`) are often signs of compromise.
- Tools like `lsof` and `netstat` can reveal hidden communications or unauthorized listening services.
- Knowing how to map a PID to file handles is useful for understanding what a suspicious process is touching — logs, config files, scripts, or sockets.
- These lightweight commands form the backbone of live incident response when time and access are limited.

---

## Why It Matters

Being able to investigate what’s happening on a machine in real time — without relying on third-party software — is critical during a breach or malware outbreak. These techniques form the foundation of endpoint visibility and help analysts decide when and how to escalate or contain a threat. This module prepares me for real-world triage using only native system tools.

---

