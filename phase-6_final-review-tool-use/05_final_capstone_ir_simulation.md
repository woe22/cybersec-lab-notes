# 05 — Final Capstone: IR Simulation

---

## Scenario

In this final capstone module, I performed a complete Tier 1 incident response simulation. I was alerted to a suspicious process running from `/tmp/`, often a sign of malware, privilege escalation, or backdoor activity. I investigated using endpoint visibility, file system forensics, and network inspection techniques.

---

## What I Did

```bash
# Identified suspicious process in /tmp
ps aux | grep /tmp/

# Traced process activity
sudo lsof -p <PID>

# Checked for outbound connections
sudo lsof -i -n -P | grep <PID>
sudo netstat -tulnp | grep <PID>

# Investigated shell history for execution source
cat ~/.bash_history | tail -n 30

# Searched for persistence mechanisms
crontab -l
ls -l /etc/cron.* /etc/init.d/ ~/.config/autostart
```

---

## What I Learned

- Suspicious binaries in `/tmp/` are a red flag, especially when paired with outbound network connections or executed via shell scripts.
- `lsof` and `netstat` can confirm if a process is communicating with external IPs — indicating possible data exfiltration or command-and-control.
- Reviewing shell history can quickly show how malware was launched, which user initiated it, and if it was done manually or via a script.
- File persistence in `crontab`, `init.d`, or `autostart` directories can indicate re-infection risks after reboot.

---

## Final Findings

| Field                    | Result                         |
|--------------------------|--------------------------------|
| Suspicious Process       | Executable in `/tmp/`          |
| Network Connections?     | Yes — outbound established     |
| Persistence Mechanism?   | None found (no crontab/etc.)   |
| Shell History Match?     | Yes — user-initiated via script|
| Severity Assessment      | **High** — confirmed execution from temp dir, outbound comms |
| Recommended Action       | Kill process, delete binary, alert IR team for deeper review  |

---

## Why It Matters

This simulation brought together everything I’ve learned throughout the OPSEC Lab Assistant system. I was able to handle an alert from start to finish — investigating, collecting evidence, evaluating risk, and recommending containment steps. These are the core duties of a Tier 1 SOC analyst, and this exercise reinforced both my technical and analytical readiness.

---
