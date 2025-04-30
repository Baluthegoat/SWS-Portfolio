---
title: "Active Directory"
description: "Active Directory Group Policy"
pubDate: 2025-04-30
heroImage: "/what-is-group-policy-in-active-directory.avif"
readingTime: "5 min read"
tags: ["Notes", "Active Directory"]
---

- **Group Policy** is a Windows feature for administrators to manage and configure user, computer, and security settings across a domain.
- **Group Policy Objects (GPOs)** are
collections of policy settings that can be applied to users or
computers, often used for security, software deployment, and system
configuration.
- GPOs are processed in a **hierarchical order**: Local > Site > Domain > Organizational Unit (OU) > Nested
OUs, with settings at lower levels overriding higher ones.
- **Order of Precedence** and options like **Enforced** and **Block Inheritance** allow fine control over which policies apply and where.
- **Security**: GPOs are powerful for defense but can be abused for attacks if misconfigured or if attackers gain rights to modify them.
- **Refresh Interval**: GPOs update every 90 minutes (with a random offset) on clients, 5 minutes on domain controllers; can be forced with `gpupdate /force`.

## Summary of Main Points

## 1. **Purpose and Power of Group Policy**

- Used to manage user and computer settings in a Windows domain.
- Essential for security, standardization, and automation in enterprise environments.
- Examples: password policies, disabling USBs, enforcing
screensavers, software deployment, restricting applications,
audit/logging policies.

## 2. **Group Policy Objects (GPOs)**

- Virtual collections of settings, uniquely identified by GUIDs.
- Can be linked to domains, sites, OUs, or nested OUs.
- Multiple GPOs can be applied to a single container; settings can be very granular.

## 3. **Order of Precedence**

- **Local Group Policy**: Overwritten by any domain-level GPOs.
- **Site Policy**: Applied to all hosts in a site.
- **Domain-wide Policy**: Applied across the domain.
- **OU Policy**: Applied to specific users/computers in an OU.
- **Nested OU Policy**: Special permissions for objects in nested OUs.
- **Link Order**: When multiple GPOs are linked to the same OU, the one with the lowest link order is processed last and takes precedence.

## 4. **Special GPO Options**

- **Enforced (No Override):** Prevents lower-level GPOs from overriding settings.
- **Block Inheritance:** Prevents higher-level GPOs from applying to a specific OU.
- **Default Domain Policy:** Highest precedence, applies to all users/computers by default.

## 5. **GPO Refresh and Application**

- Default refresh: every 90 minutes ± 30 minutes for clients, 5 minutes for domain controllers.
- Can be changed, but not recommended to be too frequent.
- Manual update with `gpupdate /force`.

## 6. **Security Considerations**

- GPOs can be exploited if attackers gain modification rights, leading to privilege escalation, lateral movement, or persistence.
- Example: Attackers modifying GPOs to add themselves as admins, run malicious scripts, or deploy malware.

## 7. **Best Practices**

- Use GPOs for defense-in-depth.
- Restrict GPO modification rights to trusted administrators.
- Regularly audit GPOs and their permissions.
- Understand and monitor GPO application and inheritance in your domain.

## In Short

**Group Policy** is a fundamental tool for 
managing and securing Windows environments, but must be carefully 
managed to prevent abuse. Understanding GPO structure, precedence, and 
security implications is crucial for both defenders and penetration 
testers.