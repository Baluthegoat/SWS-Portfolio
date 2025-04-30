---
title: "Active Directory"
description: "Security in Active Directory  "
pubDate: 2025-04-30
heroImage: "/cia-triad.svg"
readingTime: "5 min read"
tags: ["Notes", "Active Directory"]
---

- **Active Directory (AD) is central to organizational management but is insecure by default.**
- **Security in AD is about balancing the CIA Triad:** Confidentiality, Integrity, and Availability-with AD historically prioritizing Availability.
- **Hardening AD requires both built-in Microsoft features and general security best practices.**
- **Defense-in-depth is crucial:** No single measure is sufficient; multiple layers of security are needed.

## 1. **General Hardening Measures**

- **Microsoft LAPS:** Randomizes and rotates local administrator passwords to prevent lateral movement.
- **Audit Policy Settings:** Logging and monitoring are vital for detecting unauthorized changes and attacks.
- **Group Policy Security Settings:** Use GPOs to enforce account, local, software restriction, application control, and advanced audit policies.

## 2. **Patch and Update Management**

- **WSUS and SCCM:** Automate and manage patch deployment to ensure all systems are up to date and not vulnerable to known exploits.

## 3. **Account and Credential Management**

- **Group Managed Service Accounts (gMSA):** Provide secure, automatically managed credentials for services.
- **Security Groups:** Assign permissions via groups rather than individuals for easier, more secure management.
- **Account Separation:** Admins should have separate accounts for daily tasks and administrative duties, with different passwords for each.

## 4. **Password and Authentication Policies**

- **Password Complexity & Passphrases:** Enforce long, complex passwords or passphrases; standard complexity rules are not enough.
- **Multi-Factor Authentication (MFA):** Especially important for remote desktop access and privileged accounts.

## 5. **Limiting Privilege and Exposure**

- **Limit Domain Admin Usage:** Domain Admin accounts should only be used on Domain Controllers, not regular workstations or servers.
- **Audit and Remove Stale Accounts:** Regularly review and disable or remove unused accounts and objects to reduce attack surface.
- **Audit Permissions:** Periodically review who has access to what, especially admin rights and group memberships.

## 6. **Additional Security Controls**

- **Restricted Groups:** Use Group Policy to strictly control membership of privileged groups.
- **Limit Server Roles:** Don’t overload sensitive servers (like Domain Controllers) with extra roles (e.g., web services).
- **Limit Local Admin and RDP Rights:** Only grant local admin or RDP access to those who truly need it, and never to broad groups like Domain Users.

## 7. **Continuous Monitoring and Best Practices**

- **Audit Policies & Logging:** Implement robust logging and monitoring to detect suspicious activity and potential attacks.
- **Follow Microsoft’s Best Practices:** Regularly consult and implement recommendations for securing Active Directory.

## Actionable Takeaways

- **Harden AD from the start:** Don’t rely on defaults.
- **Layer defenses:** Combine multiple security controls.
- **Regularly review, audit, and update:** Both accounts and security settings.
- **Educate users and admins:** Security awareness is critical.

**In summary:**

Securing Active Directory is about proactive hardening, ongoing 
monitoring, minimizing privileges, and using Microsoft’s tools and 
policies to reduce risk. The document provides a solid foundation for AD
 security, but emphasizes that these steps are just the beginning of a 
robust defense-in-depth strategy.