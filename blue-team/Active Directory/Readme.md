# Active Directory, DNS, and DHCP Setup

This section covers the core identity and network services used to simulate a real enterprise environment. It includes:

- Active Directory Domain Services (AD DS)
- Domain Name System (DNS)
- Dynamic Host Configuration Protocol (DHCP)

These services were configured on a **Windows Server 2022** virtual machine.

---

##  Host Overview

| Role            | Hostname | IP Address  | Notes                        |
|------------------|----------|-------------|------------------------------|
| Domain Controller| `dc01`   | `10.0.0.10` | Runs AD, DNS, DHCP services  |



### Active Directory (AD DS)

- Domain: `corp.local`
- Forest root domain created during setup
- Roles:
  - Domain Admins
  - IT Support
- Sample Users:
  - `jdoe@corp.local` – Standard User
  - `admin@corp.local` – Domain Admin


---

### DNS

- Internal domain resolution for `corp.local`
- DNS zone: `corp.local`
- A Records:
  - `dc01.corp.local → 10.0.0.10`
  - `client01.corp.local → 10.0.0.101`
  - `wazuh.corp.local → 10.0.0.11`


---

### DHCP

- Scope: `10.0.0.100 – 10.0.0.200`
- Subnet: `255.255.255.0`
- Gateway: `10.0.0.1`
- DNS Server: `10.0.0.10` (local DNS)
- Reserved IPs for key infrastructure (e.g. Wazuh)

##  Screenshots Preview

> Stored in `screenshots/` folder

- `ad-users.png`: Sample users in Active Directory  
- `groups.png`: Role-based groups created  
- `dns-zone.png`: Internal DNS records  
- `dhcp-scope.png`: IP address scope setup  

---

##  Validation Checklist

- [x] Clients receive DHCP addresses automatically  
- [x] Clients resolve domain names via internal DNS  
- [x] Clients successfully join the `corp.local` domain  
- [x] Domain logins succeed on both Linux and Windows clients  
- [x] Wazuh logs show domain activity (via agent)


