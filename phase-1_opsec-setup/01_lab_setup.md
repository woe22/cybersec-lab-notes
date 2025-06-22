    # 01 — Lab Setup

## Scenario
This module focuses on setting up a secure and operational virtual lab environment using Kali Linux within VirtualBox. The goal is to ensure a strong operational security (OPSEC) foundation from the start.

## What I Did
- Downloaded Kali Linux ISO from the official website.
- Created a new virtual machine in Oracle VirtualBox.
- Assigned system resources: 4GB RAM, 2 processors, 20GB dynamically allocated storage.
- Mounted the Kali ISO and completed the installation.
- Performed post-installation steps:
  - Installed missing dependencies.
  - Updated the system:
    ```bash
    sudo apt update && sudo apt upgrade -y
    ```
  - Enabled guest additions and clipboard sharing.
- Set a legal banner for login:
    ```bash
    echo "Authorized access only. All activity may be monitored." | sudo tee /etc/issue.net
    sudo sed -i 's|#Banner none|Banner /etc/issue.net|' /etc/ssh/sshd_config
    sudo systemctl restart ssh
    ```
- Verified banner visibility by attempting SSH login.
- Changed default Kali user password using:
    ```bash
    passwd
    ```

## What I Learned
- Installing Kali Linux in a VM gives a safe, isolated environment for testing and cybersecurity practice.
- Post-installation hygiene (like updates, dependencies, clipboard control) is crucial for a stable setup.
- The SSH banner adds legal protection and serves as a deterrent — and must be configured and verified.
- Changing default passwords is a fundamental OPSEC habit that prevents easy unauthorized access.

## Why It Matters
A hardened, well-configured virtual environment provides the secure playground needed for developing cybersecurity skills. Setting up banners and changing default credentials are small, essential steps in protecting a system from basic but common threats.

