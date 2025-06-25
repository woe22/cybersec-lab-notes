# 00 — Prelude: Migration and Environment Cleanup

## Scenario
Before diving into Linux fundamentals, it's crucial to ensure the system environment is clean, hardened, and free from legacy or insecure configurations. This module establishes a secure baseline by removing unnecessary users, cleaning up default shell configs, and verifying that only essential services are running.

## What I Did
- ✅ Removed legacy Bash config files:
  ```bash
  rm -f ~/.bash_history ~/.bash_profile ~/.bashrc
  ```
- ✅ Reviewed and analyzed memory usage:
  ```bash
  ps aux --sort=-%mem | head -n 10
  ```
  No unnecessary processes identified; XFCE environment verified clean.
- ✅ Confirmed Zsh environment was active and functioning:
  ```bash
  echo $SHELL
  which zsh
  cat ~/.zshrc
  ```
- ✅ Reviewed user accounts:
  ```bash
  cut -d: -f1 /etc/passwd
  ```
  Removed unnecessary user with:
  ```bash
  sudo userdel -r [username]
  ```
- ✅ Cleaned system package cache:
  ```bash
  sudo apt autoremove -y && sudo apt clean
  ```
- ✅ Created a snapshot for a clean Phase 2 start:
  - Name: `Phase2_CleanStart`
  - Description: Minimal, hardened environment ready for Linux Essentials

## What I Learned
- Managing users and background services helps reduce attack surface.
- Zsh customization and cleanup improves operational efficiency and removes shell conflicts.
- Snapshots act as critical rollback points during system hardening and experimentation.
- Reviewing memory and process usage reveals what’s running under the hood, which is crucial for threat detection and system tuning.

## Why It Matters
Establishing a hardened and well-organized baseline protects the integrity of future work. By eliminating legacy shell configs and unused accounts, the system becomes more secure and efficient — both key traits of a SOC analyst's toolset. This also reduces noise when analyzing logs, processes, or running automated tools in later phases.

---

