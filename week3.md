
# 📅 Week 3 – Logging Setup, logrotate, syslog, journald

---

## ✅ Overview

This week focused on system logging and log management. I explored how logs are stored in Linux using `rsyslog` and `journald`, and I configured log rotation using `logrotate` to ensure that log files don’t fill up disk space over time. These tasks are critical for security auditing and system monitoring.

---

## 📝 Logging with Rsyslog

Rsyslog is responsible for collecting log messages and writing them to files in `/var/log`.

### 🔧 Commands Run

```bash
# Check if rsyslog is running
sudo systemctl status rsyslog

# View system log
less /var/log/syslog

# View authentication logs
less /var/log/auth.log


📸 Screenshot:
images/week3-rsyslog-status.png

🧾 Systemd Journaling (journalctl)

Systemd provides a powerful tool called journalctl to query logs from the systemd journal.

🔧 Useful Commands
# Show full boot log
journalctl -b

# Show real-time logs
journalctl -f

# Show logs for SSH
journalctl _COMM=sshd


📸 Screenshot:
images/week3-journalctl-ssh.png

🔁 Log Rotation with logrotate

Logrotate automatically compresses and removes old logs to save space and improve performance.

🔧 Commands & Config Check
# View logrotate config
cat /etc/logrotate.conf

# Check individual service config (e.g., apt)
cat /etc/logrotate.d/apt

# Force logrotate to run
sudo logrotate -f /etc/logrotate.conf


✅ Log rotation confirmed and tested manually.

📸 Screenshot:
images/week3-logrotate-config.png

🧠 Week 3 Reflection

This week deepened my understanding of how Linux handles system logs and why they’re essential for tracking activity, troubleshooting issues, and detecting potential intrusions.

I found it useful to compare traditional file-based logging (rsyslog) with systemd’s journal logging (journalctl). Initially, it was unclear where logs were going, but I learned that both systems coexist and serve different purposes depending on configuration.

One challenge was interpreting logrotate's behavior, especially its default schedule. For testing, I manually triggered it using the -f flag to confirm that old logs were rotated.

In future weeks, I’ll build on this by adding monitoring tools and potentially forwarding logs to a remote server.
