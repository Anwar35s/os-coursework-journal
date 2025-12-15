📅 Week 1 – System Setup and Architecture Planning
✅ Overview

In Week 1, I designed and deployed a headless Linux server environment using Ubuntu Server 22.04 LTS in VirtualBox. The server was configured with secure remote access using OpenSSH, and networking was set up using NAT and Host‑Only adapters. A system architecture diagram and command‑line evidence were produced to document the setup.

This environment will be used throughout the remaining weeks for security hardening, monitoring, and automation tasks.

🐧 Linux Distribution Selection

I selected Ubuntu Server 22.04 LTS as the operating system for the server.

Reasons for selection:

Long‑Term Support (LTS): Security updates available until 2027

Minimal server installation: No graphical interface, reduced attack surface

Strong community support: Extensive documentation and troubleshooting resources

Security features: Includes AppArmor, UFW, and unattended security updates

Industry relevance: Commonly used in enterprise and cloud environments

Alternative distributions considered:
Distribution	Reason Not Chosen
Debian	Extremely stable, but slower package updates
CentOS Stream	Rolling‑release model may introduce instability
Alpine Linux	Very lightweight, but lacks tools needed for this coursework

Ubuntu Server provided the best balance between stability, usability, and security.

🧰 Virtual Machine Configuration

The server was deployed as a headless virtual machine using VirtualBox.

Setting	Value
Virtualisation Platform	VirtualBox
Operating System	Ubuntu Server 22.04 LTS
Memory	2048 MB
CPU	2 vCPUs
Storage	15 GB (dynamically allocated)
Display	Headless (no GUI)
🌐 Network Configuration

Two network adapters were configured to separate internal access from external connectivity:

Adapter Configuration:

Adapter 1 – NAT

Provides internet access for updates and package installation

Adapter 2 – Host‑Only

Enables private SSH access from the host machine

IP Addressing:

Server Host‑Only IP: 192.168.56.102

Host IP: 192.168.56.1

SSH Port: 22

Network Interface (Host‑Only): enp0s8

Network Interface (NAT): enp0s3

This setup allows secure management while preventing direct external access to the server.

🔐 OpenSSH Server Configuration

OpenSSH was installed and enabled on the server to allow remote management.

Installation and setup:
sudo apt update
sudo apt install openssh-server
sudo systemctl enable ssh
sudo systemctl start ssh

Verification:
sudo systemctl status ssh

SSH Access Command (from host):
ssh username@192.168.56.102


SSH access was successfully established from the host machine using the Host‑Only network.
