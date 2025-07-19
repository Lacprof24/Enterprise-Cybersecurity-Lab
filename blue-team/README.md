#  Blue Team — Enterprise Defense Setup

This section documents the defensive side of my simulated enterprise cybersecurity lab, built using VirtualBox and following the ProjectSecurity.io framework. The goal is to detect, defend, and respond to simulated attacks using open-source and enterprise-grade tools.

---

##  Objective

To simulate a real-world Blue Team environment by:
- Configuring centralized logging and threat detection (Wazuh)
- Establishing core IT infrastructure (Active Directory, DNS, DHCP)
- Monitoring endpoints and detecting Red Team activities

---

## Components

| Component           | Role                                      |
|---------------------|-------------------------------------------|
| Wazuh               | Centralized SIEM & threat detection       |
| Wazuh Agents        | Endpoint monitoring (Linux & Windows)     |
| Active Directory    | Identity and access control               |
| DNS Server          | Internal name resolution for lab systems  |
| DHCP Server         | Automatic IP allocation to client VMs     |

---

##  Infrastructure Overview

| Hostname     | Role                | OS               | IP Address   |
|--------------|---------------------|------------------|--------------|
| `dc01`       | Domain Controller   | Windows Server   | 10.0.0.10    |
| `wazuh`      | Wazuh Manager       | Ubuntu Server    | 10.0.0.11    |
| `client-win` | Domain Workstation  | Windows 11       | 10.0.0.101   |
| `client-lin` | Domain Workstation  | Ubuntu Desktop   | 10.0.0.102   |

---

##  Detection Capabilities (via Wazuh)

| Simulated Attack              | Detected? | Tool Used        |
|-------------------------------|-----------|------------------|
| Brute-force login (Hydra)     |   yes     | Wazuh (auth logs) |
| Evil-WinRM remote access      |   yes     | Wazuh (event logs)|
| RDP enabled on client         |   yes     | Wazuh agent alert |
| User privilege escalation     |   yes     | Wazuh (Windows)   |

---
---

##  Future Enhancements

- Add Group Policy Objects (GPOs) to enforce password policies
- Integrate Suricata or Sysmon for deeper visibility
- Set up alerting thresholds and email notifications in Wazuh
- Monitor lateral movement and persistence techniques


##  Summary

This Blue Team setup simulates a realistic enterprise network and is actively defended by a centralized SIEM and properly configured infrastructure. It prepares defenders to:
- Monitor endpoints
- Detect lateral movement
- Respond to malicious behavior

>  Built entirely in VirtualBox as part of my cybersecurity lab.
