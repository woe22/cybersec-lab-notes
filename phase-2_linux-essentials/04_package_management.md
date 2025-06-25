# 04 — Package Management

---

## Scenario

As a Linux user in a cybersecurity environment, it is critical to understand how software is installed, updated, audited, and removed. In this module, I explored Debian-based package management tools like `apt` and `dpkg`, enabling me to maintain a secure and efficient system. These skills are necessary for deploying tools, applying patches, and managing dependencies on both production and analysis machines.

---

## What I Did

- Refreshed package indexes:
  ```zsh
  sudo apt update
  ```
- Upgraded packages:
  ```zsh
  sudo apt upgrade
  ```
- Installed and removed a test package:
  ```zsh
  sudo apt install cowsay
  cowsay 'I use apt like a pro\!'
  sudo apt remove cowsay
  sudo apt purge cowsay
  ```
- Searched and viewed package metadata:
  ```zsh
  apt search htop
  apt show htop
  ```
- Explored installed packages via dpkg:
  ```zsh
  dpkg -l | head -n 15
  dpkg -s bash
  dpkg -L bash
  ```
- Manually installed a `.deb` package (figlet):
  ```zsh
  sudo apt install figlet
  figlet "Package mastery!"
  ```
- Queried package install history:
  ```zsh
  grep " install " /var/log/dpkg.log | tail -n 10
  ```
- Audited existing packages:
  ```zsh
  apt list --installed | grep -i nmap
  ```
- Cleaned unused dependencies:
  ```zsh
  sudo apt autoremove
  ```

---

## What I Learned

- `apt` handles high-level package management (installing, upgrading, removing)
- `dpkg` is a lower-level tool that gives insight into exact installed files and metadata
- `.deb` packages can be manually installed, but may not resolve dependencies
- The package logs in `/var/log/dpkg.log` can be used for auditing system changes
- Escape characters (e.g., `\!` in Zsh) are needed when typing commands that include shell operators
- It’s important to regularly update and audit installed software to reduce attack surface

---

## Why It Matters

SOC analysts and Linux sysadmins must confidently install and manage security tools, patch vulnerabilities, and maintain operational software. Mastery of package management ensures that systems remain stable, secure, and ready for defensive or investigative work. These skills directly map to real-world job responsibilities in blue team environments.

---

