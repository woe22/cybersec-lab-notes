# 00 — Prelude: Tier 1 SOC Tool Categories

---

## Scenario

As I prepare to complete my OPSEC Lab journey, this module introduced the categories of tools used by real Tier 1 SOC analysts. Rather than diving into any single product, I learned how various tools fit into the daily monitoring and response workflow — including SIEMs, EDRs, SOAR platforms, and more.

---

## What I Did

- Reviewed the major categories of tools used in SOC environments:
  - SIEMs for log aggregation and alerting
  - EDRs/XDRs for endpoint threat detection
  - Ticketing systems for case management
  - SOAR platforms for workflow automation
  - Network tools for packet analysis and flow monitoring
  - Threat Intel tools for IOC enrichment

- Practiced mapping an incident response workflow to the tools:

| Stage              | Example Tool           | Action Taken                                  |
|--------------------|------------------------|-----------------------------------------------|
| Detection          | SIEM (e.g., Wazuh)     | Alert triggered: multiple failed logins       |
| Triage             | SIEM + Threat Intel    | Confirm user, source IP, geo, enrichment      |
| Host investigation | EDR                    | Checked commands run, user behavior           |
| Containment        | EDR or XDR             | Killed session or isolated host               |
| Ticketing/Escalate | ServiceNow / TheHive   | Documented findings and escalated             |

- Reflected on how my Phase 5 tooling (e.g., `journalctl`, `awk`, `grep`) mapped to real SOC tools like SIEMs.

---

## What I Learned

- SOC analysts use a wide range of specialized tools, each designed for a specific stage of incident response.
- Detection without triage is incomplete — tools must work together to provide context and support decision-making.
- Even before using a full SIEM or EDR, it’s possible to simulate their logic using basic Linux command-line tools.
- Building familiarity with tool categories helps map real alerts to specific investigative workflows.

---

## Why It Matters

Understanding SOC tooling categories allows me to step into a professional environment and quickly orient myself, regardless of the platform in use. Rather than focusing on one product, I now understand the functional purpose behind each layer of detection and response. This prepares me for real-world analyst roles where flexibility and cross-tool knowledge is key.

---
