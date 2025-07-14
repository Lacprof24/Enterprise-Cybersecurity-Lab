##  Lab Overview

This lab was designed to simulate a realistic enterprise network with both attack and defense components using open-source tools and virtualization. The goal was to build a fully integrated environment where I could practice both blue team and red team skills.

##  Virtual Machines

| Role               | OS / Tooling                |
|--------------------|-----------------------------|
| Attacker Server    | Kali Linux (Evil-WinRM, Hydra, NetExec, xfreerdp, SecLists) |
| Email Server       | Ubuntu Server (MailHog)     |
| SOC / SIEM Server  |Wazuh           |
| Clients            | Ubuntu Desktop, Windows 11 Enterprise |
| Domain Controller  | Windows Server 2024 (Active Directory, DNS, DHCP, User Management) |

##  Tools & Services Used

### Defensive
- **Wazuh** – Host-based SIEM with centralized logging
- **Active Directory** – Centralized domain controller with user/group policies
- **DNS Server** – Name resolution within internal network (Windows Server)
- **DHCP Server** – Dynamic IP assignment for client VMs (Windows Server)
- **MailHog** – Internal email testing and relay

###  Offensive
- **Kali Linux** tools including:
  - `evil-winrm` – Remote PowerShell access to Windows targets
  - `hydra` – Brute force login tool
  - `netexec` – Post-exploitation and lateral movement
  - `xfreerdp` – RDP brute-forcing and remote access
  - `SecLists` – Wordlists used for enumeration and attacks

##  Lab Setup Highlights

- Configured **Active Directory domain** and added Ubuntu & Windows clients
- Created **user accounts** and **organizational units** for role-based access
- Set up internal **DNS and DHCP servers** using Windows Server 2024
- Deployed Wazuh agents across all systems and forwarded logs to the manager
- Simulated real-world attacks to test visibility and detection

##  Network Design

- **VirtualBox** with both **Host-only** and **NAT** adapters
- Isolated internal enterprise-style network
- Internal name resolution, IP management, and authentication services

## Skills Gained

- Endpoint and network threat detection
- AD user/group creation, domain join, and GPO management
- DNS/DHCP deployment in a Windows Server environment
- Attacker simulation using Kali Linux tools
- Incident monitoring with Wazuh 

