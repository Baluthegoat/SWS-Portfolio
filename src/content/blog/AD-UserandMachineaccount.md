---
title: "Active Directory"
description: "User and machine account"
pubDate: 2025-04-30
heroImage: "/AD_MachineAccountQuota_01.jpg"
readingTime: "5 min read"
tags: ["Notes", "Active Directory"]
---

## User Accounts: Purpose and Management

- User accounts are created both locally and in Active
Directory (AD) to allow people or programs to log on and access
resources based on assigned rights.
- When a user logs in, their password is verified and an
access token is created, describing their security identity and group
memberships. This token is presented whenever the user interacts with
processes or resources
- Administrators often assign rights to groups instead of
individual users, simplifying privilege management and making it easier
to grant or revoke access.
- Most organizations have at least one AD user account per employee, but often more due to service accounts or multiple roles.
Disabled accounts for former or temporary employees are commonly
retained for audit purposes and stored in designated OUs (e.g., “FORMER
EMPLOYEES”)
- User accounts can be provisioned with a wide range of
rights, from basic read-only access to full domain control (Enterprise
Admin). Misconfigurations can easily grant excessive privileges,
creating a significant attack surface
- Users are often the weakest security link due to
weak/shared passwords, unauthorized software, or mismanagement.
Defense-in-depth and strong policies are needed to mitigate these risks

**Local Accounts**

- Local accounts exist only on individual systems and
manage access to resources on that host. Rights assigned to these
accounts do not extend across the domain
- Default local accounts include:
    - **Administrator:** Full control over the
    system, cannot be deleted or locked, but can be disabled or renamed.
    Disabled by default on recent Windows versions
    - **Guest:** Disabled by default, intended for temporary, limited access. Recommended to remain disabled for security
    - **SYSTEM:** Used by the OS for internal
    functions, has the highest privileges, does not appear in User Manager,
    and cannot be added to groups
    - **Network Service/Local Service:** Predefined accounts for running Windows services, with limited or anonymous network credentials

**Domain Users**

- Domain users receive rights from the domain, allowing
access to resources like file servers and printers across any
domain-joined host
- The **KRBTGT** account is a special
built-in account for Kerberos authentication, often targeted in attacks
like Golden Ticket due to its ability to grant broad domain access

**User Naming Attributes**

- Important AD user attributes include:
    - **UserPrincipalName (UPN):** Primary logon name, often the user’s email address
    - **ObjectGUID:** Unique, unchanging identifier for the user object
    - **SAMAccountName:** Legacy logon name for compatibility with older systems
    - **objectSID:** Security Identifier, used to identify users and their group memberships
    - **sIDHistory:** Stores previous SIDs, especially after domain migrations.

**Domain-Joined vs. Non-Domain-Joined Machines**

- **Domain-Joined:** Managed centrally via
the Domain Controller (DC), allowing users to log in from any
domain-joined host and receive policies and updates through Group
Policy. Typical in enterprise environments
- **Non-Domain-Joined (Workgroup):** Managed locally, suitable for home or small business use. Accounts and profiles are local to each host and not transferable

**Machine Accounts**

- Machine accounts (e.g., NT AUTHORITY\SYSTEM) in AD have
rights similar to standard domain user accounts. SYSTEM access on a
domain-joined host allows broad read access to domain data, making it a
valuable foothold for attackers

**Summary**

- User and machine accounts are foundational to AD security and resource access.
- Group-based privilege assignment simplifies management but can introduce risk if misconfigured.
- Local accounts are limited to individual hosts, while domain accounts provide centralized access and control.
- Mismanagement of accounts, especially privileged or
SYSTEM accounts, creates significant security risks and opportunities
for attackers