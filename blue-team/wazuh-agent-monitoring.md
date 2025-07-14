# Wazuh Agent-Based Monitoring

This document outlines how Wazuh was deployed to monitor host-based activity on Windows and Ubuntu machines within the lab environment.

---

##  Setup Summary

- **Wazuh Version**: 4.9.x
- **Manager IP**: `10.0.0.10`
- **Agents Installed On**:
  -  Windows Server 2024 (Domain Controller, DNS, DHCP)
    - Ubuntu Desktop (Workstation Target)

---

##  Installing the Wazuh Agent

###  On Windows:
```powershell
Invoke-WebRequest -Uri https://packages.wazuh.com/4.x/windows/wazuh-agent-4.9.2-1.msi -OutFile $env:tmp\wazuh-agent.msi
msiexec.exe /i $env:tmp\wazuh-agent.msi /q WAZUH_MANAGER='10.0.0.10' WAZUH_AGENT_GROUP='default'

On Ubuntu:
bash
Copy
Edit
curl -s https://packages.wazuh.com/4.x/install.sh | sudo bash
sudo WAZUH_MANAGER='10.0.0.10' /var/ossec/bin/agent-auth -m 10.0.0.10
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent
