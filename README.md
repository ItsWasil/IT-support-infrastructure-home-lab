# IT Support & Infrastructure Administration Home Lab

A hands-on IT Support and Infrastructure Administration project built using **Windows Server 2025** in VMware Workstation.

This project demonstrates practical skills in user account management, access control, shared folder administration, DNS configuration, Group Policy, PowerShell and basic infrastructure troubleshooting.

## Project Objectives

The objective of this project was to simulate a small company's IT infrastructure and practise common IT support and system administration tasks.

Key objectives:
- Create and manage employee accounts.
- Organize users by department.
- Configure security groups and access permissions.
- Set up departmental shared folders.
- Apply password and account lockout policies.
- Configure and troubleshoot DNS.
- Verify Windows Server and Active Directory services.

## Lab Environment

| Component | Configuration |
|---|---|
| Virtualization | VMware Workstation |
| Operating System | Windows Server 2025 Datacenter Evaluation |
| Server Name | TECHNOVA-DC01 |
| Domain Name | server2025.com |
| Domain NetBIOS Name | SERVER2025 |
| Server IP Address | 192.168.255.10 |
| Network | VMware NAT (VMnet8) |
| Main Server Role | Active Directory Domain Services |
| DNS | Windows Server DNS |

## Tasks Performed

### 1. Active Directory and User Management
- Installed and configured Active Directory Domain Services (AD DS).
- Promoted the server to a Domain Controller.
- Created an organizational structure for IT, HR, Finance and Sales.
- Created five fictional employee accounts.
- Organized employees into department-based security groups.

### 2. Department-Based Access Management
Created the following security groups:
- GG_IT_Staff
- GG_HR_Staff
- GG_Finance_Staff
- GG_Sales_Staff

Configured group memberships to organize access according to department responsibilities.

### 3. File Sharing and Permissions
- Created departmental folders under `C:\CompanyShares`.
- Configured SMB network shares.
- Applied department-specific share permissions.
- Configured NTFS permissions using security groups.
- Restricted broad access to departmental folders.

### 4. Group Policy Administration
Configured domain password policies:
- Minimum password length: 12 characters.
- Password complexity: Enabled.
- Password history: 5 passwords.
- Maximum password age: 90 days.
- Minimum password age: 1 day.

Configured account lockout policies:
- Account lockout threshold: 5 invalid attempts.
- Account lockout duration: 15 minutes.
- Account lockout observation window: 15 minutes.

### 5. DNS and Network Configuration
- Configured a static IPv4 address for the server.
- Configured the server to use its local DNS service.
- Verified forward DNS resolution.
- Verified Active Directory LDAP SRV records.
- Configured and checked DNS forwarding and delegation.
- Troubleshot DNS registration and name-resolution issues.

### 6. PowerShell Administration and Troubleshooting

Used PowerShell to manage and verify Windows Server configuration.

Examples of commands used:

```powershell
Get-Service DNS,NTDS,Netlogon,w32time

Get-ADDomain

Get-ADDomainController

Get-ADUser -Filter *

Get-ADGroup -Filter *

Get-SmbShare

Get-SmbShareAccess -Name IT

Get-ADDefaultDomainPasswordPolicy

dcdiag /test:dns /v
```

## Validation and Testing

The following checks were performed:

- Verified Active Directory domain configuration.
- Confirmed that AD DS, DNS and Netlogon services were running.
- Verified DNS host and LDAP SRV record resolution.
- Checked SMB share accessibility.
- Reviewed share and NTFS permissions.
- Verified domain password and account lockout policies.
- Ran the dedicated DNS diagnostic using `dcdiag`.

**Validation note:** The dedicated DNS diagnostic passed all six DNS categories. The full `dcdiag /v` also passed the core AD DS checks, but its SystemLog test reported warnings/errors relating to DNS registration, Secure Boot and VMware NAT communication. These findings were documented rather than represented as a completely clean diagnostic.

## Lab Limitations

- This project was implemented using one Windows Server virtual machine.
- Separate domain-joined employee workstations were not deployed.
- Therefore, full per-user access authorization testing from separate client machines was not performed.
- This is a learning lab, not a production enterprise environment.

## Skills Demonstrated

- IT Support Fundamentals
- Windows Server Administration
- Active Directory Administration
- User and Group Management
- Access Control and Permissions
- DNS Configuration and Troubleshooting
- Group Policy Management
- SMB File Sharing
- NTFS Permissions
- PowerShell Administration
- Basic Network Troubleshooting
- IT Infrastructure Support

## Conclusion

This project provided practical experience in configuring and managing a small Windows-based IT environment. It helped develop foundational skills relevant to IT Support Engineer, Desktop Support Engineer, Service Desk Analyst and Junior System Administrator roles.

**Environment:** Personal home lab  
**Platform:** VMware Workstation and Windows Server 2025
