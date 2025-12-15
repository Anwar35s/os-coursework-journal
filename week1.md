# 📅 Week 1 – System Setup and Architecture Planning

---

## ✅ Overview

In Week 1, I created a headless Linux server environment using **Ubuntu Server 22.04 LTS** within **VirtualBox**. I configured the system for remote SSH access, set up networking using both NAT and Host-Only adapters, and documented the architecture with a visual diagram. This setup forms the secure foundation for the remaining weeks of the Operating Systems coursework.

---

## 🐧 Linux Distribution Selection

I selected **Ubuntu Server 22.04 LTS** due to the following reasons:

- Long-Term Support (LTS) until 2027
- Minimal, secure server edition (no GUI)
- Strong community support and documentation
- Widely used in cloud and enterprise environments
- Comes with AppArmor, UFW, and support for unattended upgrades

### ❗ Alternatives considered:

| Distribution | Pros                        | Cons                             |
|--------------|-----------------------------|----------------------------------|
| Debian       | Very stable, lightweight    | Slower updates, less user-friendly |
| CentOS       | Enterprise-grade            | CentOS Stream introduces instability |
| Alpine Linux | Very minimal footprint      | Too lightweight for this course |

---

## 🧰 Virtual Machine Configuration

| Setting            | Value                   |
|--------------------|-------------------------|
| Virtualisation     | VirtualBox              |
| OS                 | Ubuntu Server 22.04 LTS |
| RAM                | 2048 MB                 |
| CPU Cores          | 2                       |
| Disk Size          | 15 GB (dynamically allocated) |
| Boot Mode          | Headless (CLI only)     |
| Display            | None                    |

---

## 🌐 Network Configuration

To securely access the server and allow internet access, I configured two adapters:

- **Adapter 1 – NAT:**  
  Provides internet access for system updates and package installation.

- **Adapter 2 – Host-Only:**  
  Enables private SSH access from the host machine to the VM.

### 🔐 IP Addresses

| Component      | IP Address       |
|----------------|------------------|
| Host Machine   | 192.168.56.1     |
| Ubuntu Server  | 192.168.56.102   |
| SSH Port       | 22 (default)     |

---

## 🔐 OpenSSH Server Setup

### ✅ Installation and Service Configuration

```bash
sudo apt update
sudo apt install openssh-server
sudo systemctl enable ssh
sudo systemctl start ssh

✅ SSH Status Check
sudo systemctl status ssh

✅ SSH Access from Host
ssh username@192.168.56.102


✔️ SSH access was successfully verified from the host machine to the Ubuntu VM
