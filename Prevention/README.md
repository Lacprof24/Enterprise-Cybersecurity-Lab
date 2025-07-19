#  Attack Prevention & Mitigation Strategies

This document outlines practical steps to prevent and mitigate the attacks simulated in the Red Team exercise, focusing on Windows environments monitored by Wazuh agents.

---

## 1. Prevent Network Reconnaissance

- Restrict network scanning by implementing firewall rules to block unauthorized scanning and reconnaissance tools.  
- Deploy Network Intrusion Detection Systems (NIDS) like Suricata to alert on suspicious scanning activity.  
- Use network segmentation to limit attacker visibility.

---

## 2. Mitigate Brute-Force Attacks (SMB & RDP)

- Enforce strong, complex passwords and regular password changes.  
- Enable account lockout policies to block accounts after several failed login attempts.  
- Restrict RDP and SMB access to trusted IP addresses using firewall rules or VPNs.  
- Disable unused services like SMBv1, and consider using NLA (Network Level Authentication) for RDP.  
- Monitor authentication logs actively for unusual login failures.

---

## 3. Block Unauthorized Remote Access (WinRM & RDP)

- Limit WinRM and RDP access only to authorized administrators or service accounts.  
- Enable encryption and strong authentication for remote management tools.  
- Implement multi-factor authentication (MFA) where possible.  
- Regularly audit user accounts and remove unnecessary admin privileges.

---

## 4. Enhance Endpoint Security

- Deploy and configure Sysmon to collect detailed process and network activity logs.  
- Keep all systems updated with the latest security patches.  
- Use application whitelisting to block unauthorized executables and scripts.  
- Monitor PowerShell and scripting activity; enable script block logging.

---

## 5. Improve Monitoring and Alerting

- Customize Wazuh detection rules to reduce noise and prioritize high-risk alerts.  
- Correlate logs from multiple sources (host, network, and application) for comprehensive detection.  
- Create alerting workflows to notify security teams immediately upon detection.

---

## 6. User Awareness and Training

- Conduct regular security awareness training focused on phishing and credential safety.  
- Educate users on the risks of weak passwords and unsafe remote access practices.

---
