title: Week 3 – Logging, Syslog, and Log Rotation
---

# 📅 Week 3 – Logging Setup, logrotate, syslog, journald

---

## ✅ Overview

This week focused on system logging and log management. I explored how logs are stored in Linux using `rsyslog` and `journald`, and I configured log rotation using `logrotate` to ensure that log files do not fill up disk space over time. Logging is essential for troubleshooting, auditing, and detecting security incidents.

---

## 📝 Logging with Rsyslog

Rsyslog is responsible for collecting system and application logs and storing them in `/var/log`.

### 🔧 Commands Run

```bash
sudo systemctl status rsyslog
less /var/log/syslog
less /var/log/auth.log
📸 Screenshot: rsyslog service status

📸 Screenshot: Syslog output

📸 Screenshot: Auth log (SSH activity)

🧾 Systemd Journaling (journalctl)
Systemd provides journalctl to query logs stored by the systemd journal.

🔧 Commands Run
bash
Copy code
journalctl -b
journalctl -f
journalctl _COMM=sshd
📸 Screenshot: SSH logs using journalctl

🔁 Log Rotation with logrotate
Logrotate ensures logs are automatically rotated, compressed, and removed to prevent disk exhaustion.

🔧 Commands Run
bash
Copy code
cat /etc/logrotate.conf
cat /etc/logrotate.d/apt
sudo logrotate -f /etc/logrotate.conf
ls -lh /var/log/*.gz
📸 Screenshot: logrotate main config

📸 Screenshot: logrotate apt config

📸 Screenshot: Rotated log files

🧠 Week 3 Reflection
This week improved my understanding of how Linux handles system logging and why logs are critical for both security and maintenance. Learning about rsyslog helped me understand how traditional log files such as syslog and auth.log are generated and stored.

Using journalctl was particularly useful, as it allows detailed filtering of logs by service and time. At first, I found it confusing to understand the difference between journal logs and file-based logs, but I learned that they can work together depending on system configuration.

I also gained practical experience with logrotate, especially how it manages log file size automatically. Manually forcing log rotation helped me confirm that it was configured correctly. This week showed me how proper logging and log management is essential for system stability, security auditing, and future troubleshooting.
