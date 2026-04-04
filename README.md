# CMPN202 Operating Systems Coursework Journal

**Student ID:** Z23596530  
**Module:** CMPN202 – Operating Systems  
**University:** University of Roehampton  

---

## 🔗 Live Journal

➡️ **[https://anwar35s.github.io/os-coursework-journal](https://anwar35s.github.io/os-coursework-journal)**

---

## 📋 Project Overview

This repository documents a 7-week operating systems coursework involving the deployment, configuration, security hardening, and performance evaluation of a headless Ubuntu Server 24.04.3 LTS virtual machine.

The server was administered exclusively via SSH from a Mac workstation (Option B), enforcing command-line proficiency throughout. All security controls, monitoring scripts, and benchmarks were implemented and evidenced across the weekly journal entries.

---

## 🖥️ System Architecture

| Component | Details |
|---|---|
| Hypervisor | UTM on macOS Apple Silicon |
| Server OS | Ubuntu Server 24.04.3 LTS (aarch64) |
| Server IP | 192.168.64.13 |
| Workstation | Mac Terminal (Option B) |
| Workstation IP | 192.168.64.1 |
| Network | UTM Virtual (192.168.64.0/24) |

---

## 📅 Weekly Journal

| Week | Phase | Key Deliverables | Status |
|---|---|---|---|
| [Week 1](week1.md) | System Planning | Architecture diagram, distribution justification, CLI system specs | ✅ |
| [Week 2](week2.md) | Security Planning | Threat model, security checklist, testing methodology | ✅ |
| [Week 3](week3.md) | Application Selection | 5 benchmark tools installed, application matrix, monitoring strategy | ✅ |
| [Week 4](week4.md) | Security Implementation | SSH key auth, UFW firewall, user management | ✅ |
| [Week 5](week5.md) | Advanced Security | AppArmor, fail2ban, unattended-upgrades, two scripts | ✅ |
| [Week 6](week6.md) | Performance Testing | 5 benchmark tests, optimisation analysis, performance data table | ✅ |
| [Week 7](week7.md) | Security Audit | Lynis audit (62→63), nmap scan, service inventory | ✅ |

---

## 🔐 Security Controls Implemented

| Control | Tool | Status |
|---|---|---|
| SSH key-based authentication | OpenSSH ed25519 | ✅ |
| Password authentication disabled | sshd_config | ✅ |
| Root login disabled | sshd_config | ✅ |
| Firewall — SSH from workstation only | UFW | ✅ |
| Mandatory access control | AppArmor (158 profiles enforcing) | ✅ |
| Intrusion detection | fail2ban (sshd jail) | ✅ |
| Automatic security updates | unattended-upgrades | ✅ |
| Malware scanning | rkhunter (0 rootkits found) | ✅ |
| Non-root admin user | sysadmin with sudo | ✅ |

---

## 📊 Performance Results Summary

| Test | Tool | Key Result |
|---|---|---|
| CPU stress | stress-ng | 99.35% CPU utilisation, 914 bogo ops/s |
| Memory throughput | sysbench | 11,768 MiB/sec |
| Disk I/O | fio | 66 MiB/s read, 16,900 IOPS |
| Network throughput | iperf3 | 5.18 Gbits/sec |
| Web server | nginx + ab | 11,490 req/sec baseline, 11,688 after gzip |

---

## 📜 Scripts

| Script | Location | Purpose |
|---|---|---|
| `security-baseline.sh` | Server `~/` | Verifies 10 security controls, outputs PASS/FAIL |
| `monitor-server.sh` | Mac `~/` | Collects 10 performance metrics remotely via SSH |

---

## 🧰 Tools Used

- **OS:** Ubuntu Server 24.04.3 LTS
- **Virtualisation:** UTM (Apple Silicon)
- **Security:** UFW, AppArmor, fail2ban, rkhunter, Lynis, OpenSSH
- **Benchmarking:** stress-ng, sysbench, fio, iperf3, nginx, Apache Bench
- **Monitoring:** htop, mpstat, iostat, iftop, top
- **Auditing:** Lynis 3.0.9, nmap 7.99
- **Documentation:** Markdown, GitHub Pages

---

## 📁 Repository Structure
/
├── images/              # All screenshots and evidence
├── week1.md             # System planning and architecture
├── week2.md             # Security planning and methodology
├── week3.md             # Application selection and installation
├── week4.md             # SSH, firewall, user management
├── week5.md             # AppArmor, fail2ban, scripts
├── week6.md             # Performance testing and analysis
├── week7.md             # Security audit and evaluation
├── README.md            # This file
└── Z23596530_GitHub_URL.txt

---

## 🎓 Learning Outcomes Addressed

- **LO3:** Security vulnerabilities assessed and mitigated through UFW, AppArmor, fail2ban, SSH hardening, and Lynis audit
- **LO4:** CLI proficiency demonstrated across 30+ distinct commands spanning file management, process monitoring, networking, and scripting
- **LO5:** Trade-offs analysed including security vs performance, virtualisation overhead, and ARM64 constraints

---

## 📌 Submission

- **GitHub Pages URL:** https://anwar35s.github.io/os-coursework-journal
- **Student ID:** Z23596530
- **Deadline:** Week commencing 15th December 2025

