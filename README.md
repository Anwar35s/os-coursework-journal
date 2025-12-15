# CMPN202 Operating Systems Coursework Journal

This repository contains my weekly journal for the Operating Systems module at university. It documents the planning, setup, configuration, and security hardening of a headless Linux server environment over several weeks.

---

## 🔗 GitHub Pages Journal

You can view my live coursework journal here:

➡️ https://github.com/Anwar35s/os-coursework-journal

---

## 📁 Repo Structure

/ (root of the repo)
├── index.md                      # GitHub Pages homepage
├── week1.md                      # Week 1 journal entry
├── images/                       # Folder for screenshots and diagrams
│   ├── week1-architecture.png    # Your system architecture diagram
│   └── week1-ssh-access.png      # SSH access screenshot
├── README.md                     # Intro and link to your journal
└── StudentID_GitHub_URL.txt      # File to submit to Moodle


---

## 📅 Weekly Journal Entries

| Week | Focus | Status |
|------|-------|--------|
| ✅ [Week 1](week1.md) | Server setup, distro selection, SSH, architecture diagram | Completed |
| ⏳ [Week 2](week2.md) | Threat modelling, firewall setup, update automation | In progress |
| ⏳ [Week 3](week3.md) | Logging setup, logrotate, syslog, journald | Not started |
| ⏳ [Week 4](week4.md) | File and user permissions, sudo policies, group access | Not started |
| ⏳ [Week 5](week5.md) | Monitoring tools (top, htop, ps), process management | Not started |
| ⏳ [Week 6](week6.md) | Automation with scripts, backups, cron jobs | Not started |
| ⏳ [Week 7](week7.md) | Final review, hardening recap, reflection and cleanup | Not started |

---

## 🧰 Tools & Technologies Used

- **Ubuntu Server 22.04 LTS** (headless VM)
- **OpenSSH Server & Client**
- **VirtualBox** (NAT + Host-only adapters)
- **CLI tools**: `ip`, `df`, `free`, `uname`, `lsb_release`, `ufw`, `cron`
- **Logging**: `syslog`, `journald`, `logrotate`
- **Automation**: Bash scripting, crontab
- **Documentation**: Markdown, GitHub Pages
- **Security**: CIS Benchmark, UFW, unattended-upgrades

---

## 👨‍🎓 Student Information

- **Student ID:** Z23596530  
- **GitHub Username:** [Anwar35s](https://github.com/Anwar35s)  
- **Module:** CMPN202 – Operating Systems  
- **Lecturer:** Z23596530  
- **University:** University of Roehampton

---

## ✅ Coursework Objectives

- ✔️ Secure Linux server deployment
- ✔️ Justified distro and network design choices
- ✔️ Remote management via SSH
- ✔️ Hardening with firewall and updates
- ✔️ Logging, monitoring, and auditing
- ✔️ Automation of system tasks
- ✔️ Final review and reflection
- ✔️ All evidence submitted via GitHub Pages

> 📌 Screenshots, command outputs, and configurations reflect actual work done in the virtual lab environment.
>
> ---

## 🧠 Reflection

Week 1 provided a valuable foundation for understanding how to deploy and manage a secure Linux environment. Setting up a headless Ubuntu Server VM helped me improve my confidence using the command line, especially for networking and remote access.

I faced initial issues with SSH connectivity due to VirtualBox network adapter misconfiguration. Through troubleshooting using `ip a` and checking my adapter settings, I was able to resolve the problem and establish a working SSH connection from the host.

This process reinforced the importance of proper network planning and verification. It also helped me gain hands-on experience with core tools like `systemctl`, `uname`, `df`, and `free`, and understand how to document infrastructure clearly using diagrams.

Overall, Week 1 strengthened my understanding of Linux fundamentals, system access, and virtualisation — preparing me for deeper security and system administration tasks in future weeks.

---


