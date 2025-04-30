---
title: "Active Directory"
description: "Active Directory Terminology "
pubDate: 2025-04-30
heroImage: "/ad.png"
readingTime: "5 min read"
tags: ["Notes", "Active Directory"]
---

# Active Directory Terminology

1. Object — ANY resource in an AD environment
2. Attributes — Every object has attributes associated with it. For example, a computer with have a hostname and DNS attribute. All attributes will have an LDAP name used for performing LDAP queries.
3. Scheme — think of this as the blueprint. Defines what types of objects can exist in an AD environment and their associated attributes.
4. Domain — group of objects with logical, tree-like connections. Domains operate completely independent of each other but can be linked with trust relationships.
5. Forest — collection of domains.
6. Tree — collection of AD domains beginning with a single root domain.
7. Container — hold other objects or have a defined place in a directory hierarchy.
8. Leaf — contained at the end of a subtree hierarchy
9. Global Unique Identifier (GUID) — unique 128-bit value assigned when a domain user or group is created, similar to a MAC address.
10. Security principles — security principles are domain objects that can manage access to other resources within the domain
11. Security identifier (SID) — is used as a unique identifier for a security principal or security group. Every account, group, or process has its own unique SID, which, in an AD environment, is issued by the domain controller and stored in a secure database. A SID can only be used once.Even if the security principle is deleted, it can never be used again in that environment to identify another user or group. 
12. Distinguished Name (DN) — describes full path to an object in an AD.
13. Relative Distinguished Name (RDN) — a single component of the Distinguished Name that identifies the object as unique from other objects at the current level in the naming hierarchy.
14. sAMAccountName — user’s logon name.
15. userPrincipleName — another way to identify users in AD. This attribute consists of a prefix (the user account name) and a suffix (the domain name) in the format of `bjones@inlanefreight.local`. This attribute is not mandatory.
16. FSMO Roles — Flexible Single Master Operator Roles.
17. Global Catalog (GC) — Domain controller that stores copies of all objects in a forest. This partial storage of objects in other linked branches allows for object search and authorisation.
18. Read-Only Domain Controller (RODC) — No AD passwords cached here. Also contains a read only DNS server.
19. Service Principal Name (SPN) — unique identifier for service instance used by Kerberos authentication.
20. Group Policy Objective (GPO) — virtual collections of policy settings, each with a unique GUID.
21. Access Control List (ACLs) — ordered collection of Access Control Entities (ACEs) that apply to an object.
22. ACEs — identifies a trustee and identifies access rights.
23. Fully Qualified Domain Name (FQDN) — complete name for a computer or host.
24. Tombstone — container object in AD that holds deleted objects.
25. AD Recycle Bin — This made it easier for sysadmins to restore objects, avoiding the need to restore from backups, restarting Active Directory Domain Services (AD DS), or rebooting a Domain Controller. When the AD Recycle Bin is enabled, any deleted objects are preserved for a period of time, facilitating restoration if needed.
26. SYSVOL — stores copies of public files in the domain such as system policies, Group Policy settings, logon/logoff scripts, and often contains other types of scripts that are executed to perform various tasks in the AD environment.
27. AdminSDHolder — used to manage ACLs for members of built-in groups in AD marked as privileged. It acts as a container that holds the Security Descriptor applied to members of protected groups. The SDProp (SD Propagator) process runs on a schedule on the PDC Emulator Domain Controller. When this process runs, it checks members of protected groups to ensure that the correct ACL is applied to them. It runs every hour by default.
28. dsHeuristics — a string value set on the Directory Service object used to define multiple forest-wide configuration settings. One of these settings is to exclude built-in groups from the Protected Groups list.
29. adminCount — determines whether or not the SDProp process protects a user. If the value is set to 0 or not specified, the user is not protected. If the attribute value is set to 1, the user is protected. Attackers will often look for accounts with the adminCount attribute set to 1 to target in an internal environment. These are often privileged accounts and may lead to further access or full domain compromise.
30. Active Directory Users and Computers (ADUC) — GUI console commonly used for managing users, groups, computers, and contacts in AD. Changes made in ADUC can be done via PowerShell as well.
31. ADSI Edit — GUI tool used to manage objects in AD. It provides access to far more than is available in ADUC and can be used to set or delete any attribute available on an object, add, remove, and move objects as well. It is a powerful tool that allows a user to access AD at a much deeperlevel. Great care should be taken when using this tool, as changes here could cause major problems in AD.
32. sIDHistory — holds any SIDs that an object was assigned previously. It is usually used in migrations so a user can maintain the same level of access when migrated from one domain to another.
33. NTDS.DIT — considered the heart of Active Directory. It is stored on a Domain Controller at C:\Windows\NTDS\ and is a database that stores AD data such as information about user and group objects, group membership, and, most important to attackers and penetration testers, the password hashes for all users in the domain.
34. MSBROWSE — Microsoft networking protocol that was used in early versions of Windows-based local area networks (LANs) to provide browsing services. It was used to maintain a list of resources, such as shared printers and files, that were available on the network, and to allow users to easily browse and access these resources.