# Week 2 — Security Planning and Testing Methodology

**Navigation:** [Week 1](week1.md) | Week 2 | [Week 3](week3.md) | [Week 4](week4.md) | [Week 5](week5.md) | [Week 6](week6.md) | [Week 7](week7.md)

---

## Overview

In Week 2, I designed a security baseline and performance testing methodology for my Ubuntu Server. This involved creating a performance testing plan, a security configuration checklist, and a threat model identifying key risks and mitigations. No implementation was carried out this week — this phase is purely planning to guide Weeks 4–7.

---

## 1. Performance Testing Plan

### Objective
To measure and compare Ubuntu Server resource behaviour under different workload types using remote monitoring tools executed via SSH from my Mac workstation.

### Remote Monitoring Methodology

All monitoring will be performed remotely — no direct server console access. The approach uses two methods:

**Method 1 — Live SSH monitoring:** SSH into the server and run tools such as `top`, `htop`, `iostat`, and `vmstat` interactively to observe real-time resource usage during workload execution.

**Method 2 — Automated script:** A `monitor-server.sh` script (developed in Week 5) will run on the Mac workstation, SSH into the server non-interactively, collect metrics, and log them to a timestamped file for later analysis.

### Testing Approach

Each application will be tested across four scenarios in order:

| Scenario | Description |
|---|---|
| Baseline | Server idle — no applications running. Captures normal resource usage. |
| Application load | Target application running under simulated load. |
| Bottleneck analysis | Identify which resource (CPU, RAM, I/O, network) is the limiting factor. |
| Optimisation | Apply at least two improvements and re-test to quantify the improvement. |

### Metrics to Collect

| Metric | Tool | Command |
|---|---|---|
| CPU usage | top / mpstat | `top -bn1` |
| Memory usage | free | `free -h` |
| Disk I/O | iostat | `iostat -x 1 5` |
| Network throughput | iftop / iperf3 | `iperf3 -s` |
| System latency | ping | `ping -c 10 192.168.64.1` |
| Running processes | ps | `ps aux --sort=-%cpu` |

### Baseline Measurements (Week 6 Reference)

Before any applications are installed, the following baseline values will be recorded:
- CPU idle percentage
- Available memory
- Disk read/write speeds
- Network latency to workstation

---

## 2. Security Configuration Checklist

The following checklist covers all security controls to be implemented across Weeks 4 and 5. Each item will be evidenced with screenshots and configuration file comparisons in the relevant week.

### SSH Hardening
- [ ] Generate SSH key pair on Mac workstation
- [ ] Copy public key to server (`ssh-copy-id`)
- [ ] Disable password authentication (`PasswordAuthentication no`)
- [ ] Disable root login via SSH (`PermitRootLogin no`)
- [ ] Change default SSH port (optional hardening)
- [ ] Set `MaxAuthTries 3` to limit brute force attempts
- [ ] Restrict SSH access to specific user only

### Firewall Configuration (UFW)
- [ ] Install and enable UFW (`sudo ufw enable`)
- [ ] Set default deny incoming policy
- [ ] Allow SSH only from workstation IP (`192.168.64.1`)
- [ ] Deny all other incoming connections
- [ ] Document complete ruleset with `sudo ufw status verbose`

### Mandatory Access Control
- [ ] Verify AppArmor is active (`sudo apparmor_status`)
- [ ] Ensure AppArmor is in enforce mode (not complain mode)
- [ ] Review active AppArmor profiles
- [ ] Document profile status before and after changes

### Automatic Security Updates
- [ ] Install `unattended-upgrades` package
- [ ] Configure to apply security updates automatically
- [ ] Enable automatic reboot if required
- [ ] Verify with `systemctl status unattended-upgrades`

### User Privilege Management
- [ ] Create non-root administrative user
- [ ] Add user to `sudo` group
- [ ] Lock the root account password
- [ ] Configure `sudoers` with least-privilege principle
- [ ] Test sudo access for new user

### Network Security
- [ ] Configure fail2ban for SSH intrusion detection (Week 5)
- [ ] Set ban time, find time, and max retry values
- [ ] Verify fail2ban is monitoring `/var/log/auth.log`
- [ ] Document active jails with `sudo fail2ban-client status`

---

## 3. Threat Model

I identified five security threats relevant to a headless Linux server accessed via SSH. Three are mandatory; I have included five for thoroughness.

### Threat 1 — Brute Force SSH Attack

| Field | Detail |
|---|---|
| **Threat** | Automated tools attempt thousands of password combinations to gain SSH access |
| **Likelihood** | High — SSH on default port 22 is constantly scanned on the internet |
| **Impact** | Full server compromise if successful |
| **Mitigation 1** | Disable password authentication entirely, enforce SSH key-based authentication |
| **Mitigation 2** | Install fail2ban to automatically ban IPs after repeated failed attempts |
| **Mitigation 3** | Restrict SSH access via UFW firewall to workstation IP only |
| **Implemented in** | Week 4 (SSH keys, firewall), Week 5 (fail2ban) |

---

### Threat 2 — Privilege Escalation

| Field | Detail |
|---|---|
| **Threat** | An attacker or compromised process gains root privileges from a lower-privilege account |
| **Likelihood** | Medium — depends on software vulnerabilities and misconfiguration |
| **Impact** | Complete system compromise, data destruction, persistence |
| **Mitigation 1** | Run services as non-root users with minimal permissions |
| **Mitigation 2** | Enable AppArmor mandatory access control to confine processes |
| **Mitigation 3** | Apply automatic security updates to patch kernel and privilege escalation CVEs |
| **Implemented in** | Week 4 (user management), Week 5 (AppArmor, updates) |

---

### Threat 3 — Unauthorised Network Access

| Field | Detail |
|---|---|
| **Threat** | An attacker connects to open services or ports not intended to be publicly accessible |
| **Likelihood** | High — any open port is a potential attack surface |
| **Impact** | Data exfiltration, service disruption, lateral movement |
| **Mitigation 1** | Configure UFW with default deny-incoming policy |
| **Mitigation 2** | Allow only port 22 from the specific workstation IP |
| **Mitigation 3** | Conduct regular port scans with nmap to identify unexpected open ports (Week 7) |
| **Implemented in** | Week 4 (UFW), Week 7 (nmap audit) |

---

### Threat 4 — Outdated Software with Known Vulnerabilities (CVEs)

| Field | Detail |
|---|---|
| **Threat** | Unpatched packages contain known exploitable vulnerabilities |
| **Likelihood** | High — 112 pending updates were visible at initial SSH login |
| **Impact** | Remote code execution, privilege escalation depending on the CVE |
| **Mitigation 1** | Enable `unattended-upgrades` for automatic security patch application |
| **Mitigation 2** | Run `apt upgrade` manually during each weekly session |
| **Implemented in** | Week 5 (automatic updates) |

---

### Threat 5 — Weak or Misconfigured AppArmor Profiles

| Field | Detail |
|---|---|
| **Threat** | AppArmor profiles left in complain mode or not applied, allowing unrestricted process behaviour |
| **Likelihood** | Medium — default Ubuntu installs have some profiles in complain mode |
| **Impact** | Malicious or compromised process operates without MAC restrictions |
| **Mitigation 1** | Audit all AppArmor profiles and switch to enforce mode |
| **Mitigation 2** | Use `aa-status` to regularly verify profile enforcement status |
| **Implemented in** | Week 5 (AppArmor configuration) |

---

## 4. Reflection

This week's planning phase highlighted how interconnected security controls are. For example, disabling password authentication (SSH hardening) only works effectively when combined with firewall rules restricting which IPs can attempt a connection at all. Similarly, mandatory access control via AppArmor provides a defence-in-depth layer even if an attacker bypasses authentication.

The threat model also revealed that the 112 pending updates noted at initial login represent a real and immediate risk — these will be addressed in Week 5 through automated update configuration. Planning these controls in advance ensures implementation in Weeks 4 and 5 will be systematic rather than reactive.

---

## References

[1] NIST, "Guide to General Server Security," *NIST Special Publication 800-123*, 2008. [Online]. Available: https://csrc.nist.gov/publications/detail/sp/800-123/final [Accessed: 4 Apr. 2026].

[2] Canonical Ltd., "Security - UFW," *Ubuntu Documentation*, 2024. [Online]. Available: https://help.ubuntu.com/community/UFW [Accessed: 4 Apr. 2026].

[3] fail2ban, "Fail2ban Documentation," 2024. [Online]. Available: https://www.fail2ban.org/wiki/index.php/Main_Page [Accessed: 4 Apr. 2026].


