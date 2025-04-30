---
title: "Active Directory"
description: "Active Directory Functionality"
pubDate: 2025-04-30
heroImage: "/ob.png"
readingTime: "5 min read"
tags: ["Notes", "Active Directory"]
---

# Active Directory Functionality

Active Directory FSMO (Flexible Single Master Operation) roles:

- **Schema Master:** Manages the Active Directory schema, controlling all attribute definitions for AD objects
- **Domain Naming Master:** Controls domain name management and prevents duplicate domain names in a forest
- **RID Master:** Assigns unique Relative ID blocks to domain controllers for creating object Security IDs (SIDs)
- **PDC Emulator:** Serves as the authoritative domain controller handling authentication, password changes, GPO management, and domain time synchronization
- **Infrastructure Master:** Manages cross-domain object references by translating GUIDs, SIDs, and Distinguished Names between domains

Important note: These roles can be assigned to specific domain controllers or distributed automatically when new DCs are added. If these FSMO roles malfunction, it can cause authentication and authorization problems in the domain.

## Domain Functional Levels

- Each new level inherits features from previous levels and adds new capabilities
- Windows 2000 native introduced fundamental features like universal groups and SID history
- Windows Server 2003 brought important management tools and authentication improvements
- Windows Server 2008 added critical security features including AES encryption and DFS replication
- Later versions (2012/2012 R2) focused on enhanced authentication and security features
- Windows Server 2016 introduced new credential protection and Kerberos features

## Forest Functional Levels - Key Points

- Windows Server 2003 forest level introduced crucial features:
    - Forest trusts
    - Domain renaming
    - Read-only domain controllers (RODC)
- Windows Server 2008 R2 introduced the Active Directory Recycle Bin
- Windows Server 2016 added Privileged Access Management (PAM)

Important Notes
Windows Server 2019 did not introduce a new functional level, but requires:

- Minimum of Windows Server 2008 functional level
- DFS-R for SYSVOL replication

## Backward Compatibility

Each functional level supports specific Domain Controller operating systems:

- Newer DC operating systems can operate in domains with lower functional levels
- Raising functional levels may restrict which OS versions can act as Domain Controllers
- Higher functional levels enable more advanced features but reduce backward compatibility

## Security Evolution

The progression of functional levels shows increasing focus on security:

- Early levels: Basic authentication and group management
- Middle levels: Enhanced encryption and delegation controls
- Recent levels: Advanced protection mechanisms and credential security

### Trusts

Trusts are used to establish a domain-domain or forest-forest authentication. Trusts create a link between the authentication systems of two domains.

| Trust Type | Description |
| --- | --- |
| Parent-child | Domains within the same forest. The child domain has a two-way transitive trust with the parent domain. |
| Cross-link | A trust between child domains to speed up authentication. |
| External | A non-transitive trust between two separate domains in separate forests which are not already joined by a forest trust. This type of trust utilizes SID filtering. |
| Tree-root | A two-way transitive trust between a forest root domain and a new tree root domain. They are created by design when you set up a new tree root domain within a forest. |
| Forest | A transitive trust between two forest root domains. |

![image](/images/turst.png)

## Trust Directionality

- Two-way (Bidirectional) Trust:
    - Users from both domains can access resources in either domain
    - Most common in parent-child relationships
- One-way Trust:
    - Users in trusted domain can access resources in trusting domain
    - Trust direction is opposite to access direction

## Trust Transitivity

- Transitive Trust:
    - Trust extends to objects that child domain trusts
    - Creates chain of trust relationships
    - Common in forest configurations
- Non-transitive Trust:
    - Trust limited to directly connected domains
    - No automatic trust extension to other domains

## Security Concerns

Common Trust Security Issues:

- Improper trust configurations creating unintended attack paths
- Lack of regular trust relationship reviews
- Mergers and acquisitions introducing security risks through bidirectional trusts
- Potential for external Kerberoasting attacks affecting principal domain

## Best Practices

- Regular audit of trust relationships
- Careful consideration before establishing bidirectional trusts
- Security review of trust relationships after corporate mergers
- Minimum necessary trust principle implementation
- Regular assessment of administrative access across trust boundaries