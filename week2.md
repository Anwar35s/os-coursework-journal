Week 2 – Security Planning and Testing Methodology
Performance Testing Plan

Performance testing for this coursework will be carried out remotely from a separate workstation system using SSH. The server system will operate headless without a graphical user interface, which reduces resource overhead and reflects how Linux servers are commonly deployed in professional environments. All monitoring and testing commands will therefore be executed remotely to ensure that collected performance data accurately represents system behaviour under different workloads.

The performance metrics selected for evaluation focus on the core operating system resources that directly affect system performance and reliability. These metrics include CPU utilisation, memory usage, disk input/output performance, and network latency and throughput. Measuring these metrics allows for the identification of system bottlenecks and provides quantitative evidence to support optimisation decisions made in later phases of the coursework.

Command-line monitoring tools have been selected due to their low overhead and suitability for remote system administration. CPU and process activity will be monitored using tools such as top and htop, while memory usage will be measured using free -h. Disk I/O performance will be analysed using iostat, and network performance will be assessed using ping for latency measurements and iperf3 for throughput testing. These tools are widely used in industry and provide reliable, repeatable performance data.

Performance testing will follow a structured methodology consisting of three stages. First, baseline measurements will be collected while the system is idle to establish a reference point. Second, controlled workload testing will be conducted using selected applications to generate CPU, memory, disk, and network load. Finally, post-optimisation testing will be performed after configuration changes, allowing performance results to be compared against the baseline and enabling the effectiveness of optimisations to be quantified.

Security Configuration Checklist

The following security configuration checklist defines the baseline security controls that will be implemented and verified throughout this coursework. These controls are based on industry best practices for securing Linux server systems and are designed to minimise the system’s attack surface while maintaining usability.

Security Area	Planned Configuration	Security Rationale
SSH Hardening	Enable key-based authentication, disable password authentication, disable root login	Prevents brute-force attacks and unauthorised access
Firewall Configuration	Configure firewall to allow SSH access only from the workstation IP	Reduces exposed attack surface
Mandatory Access Control	Enforce AppArmor profiles	Restricts application capabilities and limits impact of compromise
Automatic Updates	Enable unattended security updates	Minimises exposure to known vulnerabilities
User Privilege Management	Use a non-root administrative user with sudo privileges	Enforces the principle of least privilege
Network Security	Minimise running services and restrict open ports	Prevents unnecessary network exposure

This checklist provides a clear security baseline that will guide the implementation and verification of security controls in later phases of the coursework.

Threat Model

A threat model was developed to identify realistic security threats applicable to a remotely administered Linux server and to define appropriate mitigation strategies.

Threat	Description	Potential Impact	Mitigation Strategy
SSH Brute-Force Attacks	Automated attempts to guess SSH login credentials	Unauthorised system access	SSH key-based authentication and fail2ban
Privilege Escalation	Abuse of excessive user or root privileges	Full system compromise	Non-root administration and controlled sudo access
Network Reconnaissance	Port scanning to identify exposed services	Targeted exploitation	Firewall rules and service minimisation

This threat model informs the security decisions made throughout the coursework, ensuring that security controls are implemented proactively rather than reactively.

Reflection

This phase highlighted the importance of planning security and performance strategies before system implementation. By defining a clear performance testing methodology, security baseline, and threat model early in the coursework, later configuration and optimisation decisions can be structured, justified, and evaluated using quantitative evidence. This planning-first approach reflects professional system administration practices and provides a strong foundation for secure and efficient server operation.
