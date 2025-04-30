---
title: "Active Directory"
description: "Active Directory Rights and Privilage"
pubDate: 2025-04-30
heroImage: "/privileges.webp"
readingTime: "5 min read"
tags: ["Notes", "Active Directory"]
---

## 1. **Difference Between Rights and Privileges**

- **Rights**: Permissions to access objects (e.g., files, folders).
- **Privileges**: Permissions to perform actions (e.g., run programs, shut down systems, reset passwords).
- In Windows, "User Rights Assignment" refers to privileges, not just access rights.

## 2. **Importance of Proper Management**

- Mismanagement of rights and privileges is a common security flaw and can be exploited by attackers.
- Excessive group memberships and privileges are frequent issues in AD environments.

## 3. **Built-in AD Security Groups**

- **Account Operators**: Can create/modify most accounts except high-privilege ones.
- **Administrators**: Full, unrestricted access to computers or domains.
- **Backup Operators**: Can back up/restore files and log onto DCs; can extract sensitive data.
- **DnsAdmins**: Access to DNS configurations.
- **Domain Admins**: Full domain administration; members are local admins on all domain-joined machines.
- **Domain Computers/Controllers/Guests/Users**: Default groups for respective object types.
- **Enterprise Admins**: Highest privilege, forest-wide changes (e.g., add domains/trusts).
- **Event Log Readers**: Can read event logs.
- **Group Policy Creator Owners**: Can create/edit/delete Group Policy Objects.
- **Hyper-V Administrators**: Full access to Hyper-V, can impact virtual DCs.
- **IIS_IUSRS**: Used by IIS.
- **Pre–Windows 2000 Compatible Access**: Legacy group, can expose AD info.
- **Print Operators**: Manage printers on DCs, can be used for privilege escalation.
- **Protected Users**: Enhanced protections against credential theft.
- **Read-only Domain Controllers**: Contains all RODCs.
- **Remote Desktop/Management Users**: RDP/WinRM access.
- **Schema Admins**: Can modify the AD schema (very powerful).
- **Server Operators**: Can manage domain servers, access SMB shares, backup files.

## 4. **Group Scope and Membership**

- Some groups (e.g., Domain Admins) are **Global**; others (e.g., Server Operators) are **Domain Local**.
- Be cautious about who is added to privileged groups; attackers often target these.

## 5. **User Rights Assignment**

- Rights and privileges can be assigned via group membership or Group Policy (GPO).
- Examples of sensitive privileges:
    - **SeRemoteInteractiveLogonRight**: RDP access.
    - **SeBackupPrivilege**: Backup system files (can be used to dump credentials).
    - **SeDebugPrivilege**: Debug processes (can be used to extract credentials from memory).
    - **SeImpersonatePrivilege**: Impersonate tokens (used in privilege escalation attacks).
    - **SeLoadDriverPrivilege**: Load/unload drivers (possible system compromise).
    - **SeTakeOwnershipPrivilege**: Take ownership of files/objects.

## 6. **Viewing User Privileges**

- Use `whoami /priv` to list current user privileges.
- Elevated (administrator) sessions show more privileges due to User Account Control (UAC).
- Standard users have limited rights; admins have many more when running elevated.

## 7. **Security Implications**

- Assigning the wrong privilege or group membership can lead to full system or domain compromise.
- Regularly audit group memberships and user rights.
- Use least privilege principle: only assign necessary rights/privileges.

## Summary Table: Common Privileged Groups

| Group Name | Typical Rights/Privileges |
| --- | --- |
| Administrators | Full control over domain/computer |
| Domain Admins | Full domain admin, local admin on all domain machines |
| Enterprise Admins | Forest-wide configuration, highest privilege |
| Backup Operators | Backup/restore files, log on to DCs |
| Server Operators | Manage domain servers, backup files, access shares |
| Schema Admins | Modify AD schema |
| DnsAdmins | Manage DNS |
| Print Operators | Manage printers, can escalate to DC compromise |

**In summary:**

Understanding and properly managing rights and privileges in AD is critical for security. Built-in groups confer powerful abilities, and 
improper assignments can lead to privilege escalation or domain 
compromise. Always follow the principle of least privilege and audit 
group memberships and user rights regularly.