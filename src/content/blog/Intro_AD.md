---
title: "Introduction to Active Directory"
description: "Introduction and history of Active Directory"
pubDate: 2025-04-29
heroImage: "/ad.png"
readingTime: "5 min read"
tags: ["Notes", "Active Directory"]
---


# Why Active Directory ?

It is a distributed, hierarchical structure that allows for centralized management of an organization’s resources, including users, computers, groups, network devices, file shares, group policies, devices, and trusts. AD provides authentication and authorization functions within a Windows domain environment.

## Core Components

- Centralized authentication and authorization service
- Manages domain resources and policies
- Hierarchical database structure

## Critical Security Issues

Inherent Design Weaknesses:

- Read-only database accessible to all domain users
- Backward compatibility compromises security
- Not secure by default configuration
- High misconfiguration potential

## Attack Vectors

- Domain enumeration with basic user accounts
- Lateral movement exploitation
- Privilege escalation opportunities
- NoPac attack vulnerability (2021)

Technically many of its features are easy to misconfigure due to its backwards compatibility and a lot of the default options are not actually secure. Active Directory (AD) can be generally thought of as a sizeable read-only database accessible by all users in a domain, irrespective of privilege level.

Active Directory makes the information easy to find and use for administrator and users. 

## Active Directory Organization

Active Directory (AD) organization involves structuring a network into domains, trees, and forests, and then using organizational units (OUs) to manage resources efficiently. This structured approach simplifies administration, policy application, and security control. Active Directory is used by approximately 95% of Fortune 500 companies, making it a prime target for attackers. 

Active Directory has several inherent weaknesses including:
1. Read-only database accessible to all domain users.
2. Security compromises due to backward compatibility.
3. Default configurations that aren't secure.

Common Attack Vectors:

1. Domain enumeration with basic user access
2. Lateral movement exploitation
3. Privilege escalation opportunities⁠

⁠

The recent critical threats: Ransomware groups like Conti have exploited AD vulnerabilities (PrintNightmare, Zerologon) for network compromise

So therefore, Understanding AD's structure and functionality is crucial for both offensive and defensive security roles, as it's central to enterprise network security⁠. 

## History of Active Directory

Early Foundation:

- 1971: LDAP (foundation of AD) introduced in RFCs
- 1993: Novell Directory Services released, based on X.500 concept
- 1990: Microsoft's first directory services attempt with Windows NT 3.0
- 1997: First beta release of Active Directory

Major Developments:

- 2000: AD officially integrated into Windows Server
- 2003: Introduction of Forest feature for container management
- 2008: ADFS (Active Directory Federation Services) launched for SSO capabilities
- 2016: Major updates including:
    - Cloud migration capabilities
    - Enhanced security features
    - Group Managed Service Accounts (gMSA)
    - Azure AD Connect for Office 365 integration

![image.png](/images/ad.jpg)

Current State:

- Dominates enterprise directory services with 95% usage in Fortune 500 companies
- Faces ongoing security challenges and regular discovery of new vulnerabilities
- Remains crucial despite cloud transitions
- Requires constant monitoring and updates for security maintenance