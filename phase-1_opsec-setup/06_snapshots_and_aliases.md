# 05 — Snapshots and Aliases

## Scenario
Maintaining a secure and recoverable environment is essential for consistent cybersecurity practice. In this module, I created a VirtualBox snapshot to preserve the current state of my Kali Linux VM and added useful Zsh aliases to speed up routine terminal tasks. These steps enhance both security and efficiency in the lab.

## What I Did
- Used **VirtualBox** to take a snapshot of my Kali VM:
  - Snapshot name: `Phase-1-Finalized`
  - Description: A clean backup point before beginning Phase 2.
- Opened my `.zshrc` configuration file:
  ```bash
  nano ~/.zshrc
  ```
- Appended the following custom aliases:
  ```zsh
  alias update='sudo apt update && sudo apt upgrade -y'
  alias cls='clear'
  alias snapshot-reminder='echo Remember to take a snapshot before major changes!'
  ```
- Reloaded `.zshrc`:
  ```bash
  source ~/.zshrc
  ```
- Successfully tested:
  - `update`
  - `cls`
  - `snapshot-reminder`

## What I Learned
- VirtualBox **snapshots** provide a fast, reliable way to revert changes and recover from misconfigurations or system failures.
- **Aliases** improve terminal productivity by reducing repetitive typing and simplifying longer commands.
- `.zshrc` is the Zsh shell configuration file used for customizing shell behavior and defining aliases.
- Customizing the shell environment enhances usability and creates a more efficient workflow.

## Why It Matters
Snapshots are a key tool for risk mitigation — essential in cybersecurity labs where mistakes can cause system instability. Meanwhile, aliases support operational efficiency, which is critical when working in fast-paced environments like SOCs or during security assessments. Both are small steps that significantly improve a cybersecurity practitioner's workflow and OPSEC hygiene.

---

