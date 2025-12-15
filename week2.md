# 🛡️ Week 2 – Security Planning & Testing Methodology

---

## 🎯 Performance Testing Plan

### 🔹 Overview

Performance testing for this coursework will be carried out **remotely from a dedicated workstation** using **SSH**. The server system operates **headless (no GUI)** to minimise resource overhead and to mirror real-world Linux server deployments used in industry.

All monitoring and testing commands will be executed remotely via the command line. This ensures that performance data reflects **true system behaviour** under load and is not affected by local graphical processes.

---

### 📊 Metrics to Be Measured

The following operating system metrics will be monitored, as they directly impact system performance and reliability:

* **CPU utilisation** – to identify compute bottlenecks
* **Memory usage** – to detect RAM pressure and swapping
* **Disk I/O performance** – to analyse storage throughput and latency
* **Network latency** – to measure responsiveness
* **Network throughput** – to evaluate data transfer capacity

---

### 🧰 Monitoring Tools & Justification

Command-line tools are selected due to their **low overhead**, accuracy, and suitability for remote administration:

| Tool           | Purpose                              |
| -------------- | ------------------------------------ |
| `top` / `htop` | Real-time CPU and process monitoring |
| `free -h`      | Snapshot of memory usage             |
| `iostat`       | Disk I/O analysis                    |
| `ping`         | Network latency measurement          |
| `iperf3`       | Network throughput testing           |

These tools are widely used in professional environments and provide **repeatable, reliable performance measurements**.

---

### 🔁 Testing Methodology

Performance testing will follow a structured three-stage approach:

1. **Baseline Testing** – Metrics collected while the system is idle
2. **Load Testing** – Controlled workloads generate CPU, memory, disk, and network stress
3. **Post-Optimisation Testing** – Results compared against the baseline to quantify improvements

This methodology enables systematic performance analysis and evidence-based optimisation.

---

## 🔐 Security Configuration Checklist

The following checklist defines the **security baseline** that will be implemented and verified in later phases. These controls align with **industry best practices** for securing Linux servers.

| 🔒 Security Area             | Planned Configuration                                               | 🎯 Rationale                                 |
| ---------------------------- | ------------------------------------------------------------------- | -------------------------------------------- |
| **SSH Hardening**            | Key-based authentication, disable password auth, disable root login | Prevents brute-force and unauthorised access |
| **Firewall**                 | Allow SSH only from workstation IP                                  | Minimises exposed attack surface             |
| **Mandatory Access Control** | Enforce AppArmor profiles                                           | Restricts application capabilities           |
| **Automatic Updates**        | Enable unattended security updates                                  | Reduces vulnerability window                 |
| **User Privileges**          | Non-root admin user with sudo                                       | Enforces least privilege                     |
| **Network Security**         | Minimise services and open ports                                    | Limits network exposure                      |

This checklist ensures security is **planned consistently** before implementation.

---

## ⚠️ Threat Model

The threat model identifies **realistic risks** to a remotely administered Linux server and defines appropriate mitigation strategies.

| 🚨 Threat                  | Description                   | Impact                 | 🛠️ Mitigation                  |
| -------------------------- | ----------------------------- | ---------------------- | ------------------------------- |
| **SSH Brute-Force**        | Automated login attempts      | Unauthorised access    | SSH keys + fail2ban             |
| **Privilege Escalation**   | Abuse of excessive privileges | Full system compromise | Non-root admin + sudo control   |
| **Network Reconnaissance** | Port scanning of services     | Targeted exploitation  | Firewall + service minimisation |

By identifying threats early, security controls can be implemented **proactively rather than reactively**.

---

## 🧠 Reflection

This phase emphasised the importance of **planning security and performance strategies before implementation**. Defining a testing methodology, security baseline, and threat model early ensures that later configuration decisions are structured, justified, and measurable.

This planning-first approach reflects **professional system administration practices** and provides a strong foundation for secure and efficient server operation in subsequent phases.

---

✅ **Status:** Week 2 complete and aligned with assessment criteria
