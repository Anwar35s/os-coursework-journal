---
layout: default
title: Week 2 – Threat Modelling & Security Hardening
---

# 📅 Week 2 – Threat Modelling, Firewall Setup & Automatic Updates

---

## ✅ Overview

In Week 2, I focused on improving the security posture of my Ubuntu Server VM. This involved identifying potential threats through threat modelling, setting up a firewall using `ufw` (Uncomplicated Firewall), and enabling automatic security updates using `unattended-upgrades`. These actions ensure the system is protected from unauthorized access and stays updated against vulnerabilities.

---

## 🔐 Threat Modelling

Before applying configurations, I identified key threats to the server and planned appropriate mitigations.

| Threat                      | Description                                                  | Mitigation                            |
|----------------------------|--------------------------------------------------------------|----------------------------------------|
| Brute-force SSH attacks    | Repeated login attempts to gain SSH access                   | Use UFW to allow only SSH, block others |
| Unpatched vulnerabilities  | Outdated packages exposing known exploits                    | Enable automatic security updates      |
| Open/unused ports          | Unused ports can be exploited by attackers                   | Only allow necessary ports (e.g., SSH) |
| Misconfigured firewall     | Allowing broad access can increase risk                      | Define minimal firewall rules          |

---

## 🔥 Firewall Setup using UFW

To reduce the attack surface, I installed and configured `ufw` to allow only SSH connections.

### 🔧 Commands Run:

```bash
sudo apt update
sudo apt install ufw
sudo ufw allow ssh
sudo ufw enable
sudo ufw status verbose
✅ I confirmed UFW is active and only allowing SSH on port 22.

📸 Screenshot: UFW Status

♻️ Enabling Unattended Security Updates
To ensure my system receives critical security patches automatically, I enabled unattended-upgrades.

🔧 Commands Run:
bash
Copy code
sudo apt install unattended-upgrades
sudo dpkg-reconfigure --priority=low unattended-upgrades
Then I checked the logs:

bash
Copy code
less /var/log/unattended-upgrades/unattended-upgrades.log
This log confirmed that packages were downloaded and installed automatically.

📸 Screenshot: Upgrade Logs

🧠 Reflection
This week taught me the basics of system hardening in Linux. Initially, I wasn’t aware of the ufw tool, but after configuring it, I realised how simple and effective it is for reducing open ports.

I also learned about the importance of keeping a server patched. Rather than manually running updates, the unattended-upgrades service helps automate this — which is crucial for long-term maintenance.

One small challenge was locating the upgrade logs to confirm the service was active. I eventually found them in /var/log/unattended-upgrades/, which I’ll remember for future debugging.

These foundational security tasks will serve as a base for the more advanced configurations in the coming weeks.
