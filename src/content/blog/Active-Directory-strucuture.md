---
title: "Active Directory structure"
description: "Active Directory Structure"
pubDate: 2025-04-30
heroImage: "/ad.png"
readingTime: "5 min read"
tags: ["Notes", "Active Directory"]
---

## Active Directory Structure

Active Directory (AD) structure is a hierarchical system for managing users, computers, and other resources on a Microsoft Windows network. It uses a logical structure of domains, trees, and forests to organize and manage network resources, enabling centralized administration and improved security.

Active Directory Domain Services gives an organisation a way to store directory data, making it available to both standard and admin users within the same network.

## Core Security Concerns

- AD acts as a centralized database accessible to all domain users
- Even basic user accounts can perform extensive enumeration
- Misconfigurations can lead to security breaches

## Potential Attack Paths

- Initial network access (foothold)
- Lateral movement across systems
- Vertical privilege escalation
- Unauthorized resource access

## Enumerable Objects

Basic AD accounts can enumerate:

- Domain Computers
- Domain Users
- Group Information
- Organizational Units
- Domain Policy
- Domain Levels
- Password Policy
- Group policy objects (GPOs)
- Domain Trusts
- Access control lists (ACLs)

Understanding Active Directory structure is essential before attempting to exploit it, the principle is “To break it effectively, first learn how to build it"

Active Directory is arranged in a hierarchical tree structure where :

**Forest Level**

The forest represents the highest level in Active Directory's hierarchy and serves as the security boundary for all administrative control.

**Domain Level**

- Contains multiple domains and sub-domains
- Manages contained objects:
    - Users
    - Computers
    - Groups

**Organizational Units (OUs)**

Built-in OUs include:

- Domain Controllers
- Users
- Computers

```bash
																																												Active Directory Structure
INLANEFREIGHT.LOCAL/
├── ADMIN.INLANEFREIGHT.LOCAL
│
├── GPOs
│
└── OU
│
└── EMPLOYEES
│
├── COMPUTERS
│
│
└── FILE01
│
├── GROUPS
│
│
└── HQ Staff
│
└── USERS
│
└── barbara.jones
├── CORP.INLANEFREIGHT.LOCAL
└── DEV.INLANEFREIGHT.LOCAL
```

OUs can be customized by creating:

- New organizational units
- Sub-OUs
- Specific group policies for each OU

This hierarchical structure enables efficient organization and management of network resources through centralized administration. INLANEFREIGHT.LOCAL is the root domain with sub-domains of ADMIN.INLANEFREIGHT.LOCAL, CORP.INLANEFREIGHT.LOCAL, and DEV.INLANEFREIGHT.LOCAL.

The multiple domains linked together via trust relationships in organizations that perform a lot of acquisitions that is often quicker and easier to create a trust relationship with another domain/forest than recreate all new users in the current domain.

![image](/images/Active-Directory-Structure.webp)

It is common to see multiple domains (or forests) linked together via trust relationships in organizations that perform a lot of acquisitions. It is often quicker and easier to create a trust relationship with another domain/forest than recreate all new users in the current domain. As we will see in later modules, domain trusts can introduce a slew of security issues if not appropriately administered.

![domain](/images/domain.png)