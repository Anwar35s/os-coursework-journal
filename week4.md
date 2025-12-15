Week 4 – Secure Remote Access (SSH) & Permissions
---

# 🎯 Week 4 – Secure Remote Access (SSH) & Permissions

---

## 📌 Overview

This week focused on configuring secure remote access to an Ubuntu Server using **OpenSSH**, and managing Linux users, groups, permissions, and sudo privileges. These are essential for securing a multi-user server environment.

---

## 🌐 Network Configuration

The server was assigned a static IP address for reliable SSH access.

### 🛠️ Commands Used

```bash
ip a
hostname -I
🔐 SSH Service Setup
Verified and enabled the SSH service:

bash
Copy code
sudo apt update
sudo apt install openssh-server
sudo systemctl enable ssh
sudo systemctl status ssh
📸 Sudo service status:


🔑 SSH Key-Based Authentication
SSH key generated for secure login:

bash
Copy code
ssh-keygen -t ed25519 -C "cmpn202-key"
Public key added to server via:

bash
Copy code
ssh-copy-id user@server-ip
🛡️ SSH Security Hardening
Configuration changes applied in /etc/ssh/sshd_config:

text
Copy code
PubkeyAuthentication yes
PasswordAuthentication no
PermitRootLogin no
Restarted SSH:

bash
Copy code
sudo systemctl restart ssh
✅ Password login disabled
✅ Root login disabled
✅ Key-only authentication enabled

💻 Remote SSH Login Test
SSH login tested from host:

bash
Copy code
ssh anwar35s@192.168.64.14
🔧 User & Group Permissions Setup
👥 Users and Groups Created
bash
Copy code
sudo adduser student1
sudo adduser student2
sudo groupadd sharedgroup
sudo usermod -aG sharedgroup student1
sudo usermod -aG sharedgroup student2
📸 Users created:


📸 Groups added:


📁 Shared Directory Setup
Created and configured shared directory /shared:

bash
Copy code
sudo mkdir /shared
sudo chown :sharedgroup /shared
sudo chmod 770 /shared
ls -ld /shared
📸 Shared directory setup:


🔐 Sudo Privileges Check
Checked user permissions:

bash
Copy code
groups student1
sudo -l
📸 Sudo privileges:


👤 User Switch to student1
Switched users with su:

bash
Copy code
su - student1
📸 Switched to student1:


📄 student1 Creates File
File created in /shared:

bash
Copy code
touch /shared/file_by_student1.txt
📸 File created:



📂 student2 Accesses File
Logged in as student2 and accessed file:

bash
Copy code
cat /shared/file_by_student1.txt
📸 Accessed by student2:


🧠 Reflection
This week was hands-on with configuring secure SSH access and managing user permissions. SSH hardening made the server more secure by eliminating password and root logins.

I also practiced setting up a shared folder using Linux groups. Initially, I forgot to use -aG when assigning users to groups, which replaced their groups entirely. After correcting this, I successfully tested shared access between two users.

This week strengthened my knowledge of system security and access control — critical skills for managing real-world servers.

