#  Vulnerable Environment Setup

This document explains how I built and configured the vulnerable systems within my cybersecurity lab. These systems acted as targets for Red Team attacks and detection points for the Blue Team.

---

##  Virtual Machines Used

| VM             | OS                  | Purpose                     |
|----------------|---------------------|-----------------------------|
| Windows Server | Windows Server 2024 | Domain Controller, DNS, DHCP |
| Ubuntu Desktop | Ubuntu 22.04        | Simulated User Workstation  |

---

## Misconfigurations Introduced

### Windows Server:
- Enabled **RDP** with **no lockout policy**
- Created users with **weak passwords** (e.g., `November`)
- Left **WinRM enabled** (used for remote PowerShell access)
- Shared sensitive files over SMB

### Ubuntu Desktop:
- Enabled **SSH** with default config
- Created local users with weak credentials
- No firewall enabled

---

## Services Exposed

| Service | Port | Vulnerability |
|---------|------|---------------|
| RDP     | 3389 | Weak creds, brute-force possible |
| WinRM   | 5985 | Exposed, remote shell if creds found |
| SMB     | 445  | Exposed shares, user enum possible |
| SSH     | 22   | Password auth enabled, weak creds |

---

##  Sample User Accounts

| Username | Role        | Password     |
|----------|-------------|--------------|
| jdoe     | Linux User  |  november    |
| Jdoe     | Win User    |  november    |

> _Note: Passwords were selected to simulate realistic, weak enterprise environments for Red Team testing._



