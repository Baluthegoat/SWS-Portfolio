---
title: "Active Directory"
description: "Active Directory Objective"
pubDate: 2025-04-30
heroImage: "/ob.png"
readingTime: "5 min read"
tags: ["Notes", "Active Directory"]
---

# Active Directory Objects

Any resource in Active Directory environment (users, OUs, printers, domain controllers, etc.). 

![image](/images/objective.png)

## Types of Objects

- **Users**
    - Security principals with SID and GUID
    - Up to 800+ possible attributes (display name, login time, email, etc.)
    - Prime targets for attackers (even low-privileged accounts allow domain enumeration)
- **Contacts**
    - Represent external users with contact information
    - Not security principals (have GUID only, no SID)
    - Example: vendor or customer contact cards
- **Printers**
    - Represent physical printers on the network
    - Not security principals (GUID only)
    - Contain attributes like name, driver info, port number
- **Computers**
    - Any workstation or server joined to AD
    - Security principals with SID and GUID
    - Attractive targets as SYSTEM access grants domain enumeration capabilities
- **Shared Folders**
    - Point to folders on specific computers
    - Not security principals (GUID only)
    - Can have varied access controls (open to all, authenticated users only, or restricted)
- **Groups**
    - Security principals with SID and GUID
    - Contain users, computers, and other groups
    - "Nested groups" can lead to unintended privilege escalation
    - BloodHound tool useful for auditing group membership
- **Organizational Units (OUs)**
    - Administrative containers for similar objects
    - Used for delegating tasks without granting full admin rights
    - Useful for applying Group Policy to specific sets of objects
    - Example: department-based OUs (Marketing, HR, Finance, etc.)

- **Domain**: Overall structure containing objects, with its own database and policies
- **Domain Controllers**: "Brains" of AD handling authentication and access control
- **Sites**: Sets of computers across subnets used for efficient replication
- **Built-in**: Container for default AD groups
- **Foreign Security Principals**: Placeholders for objects from trusted external forests