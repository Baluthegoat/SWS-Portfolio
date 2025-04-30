---
title: "Active Directory"
description: "Active Directory Protocols"
pubDate: 2025-04-30
heroImage: "/ob.png"
readingTime: "6 min read"
tags: ["Notes", "Active Directory"]
---

Active Directory relies on four essential protocols:

### 1. Kerberos Authentication

- **Fundamentals**:
    - Default authentication protocol since Windows 2000
    - Open standard allowing interoperability
    - Uses ticket-based authentication (no password transmission)
    - Operates on port 88 (TCP/UDP)
    - Features mutual authentication (both client and server verify identities)
- **Authentication Process**:
    1. User login → Password encrypts timestamp → KDC verifies
    2. KDC issues Ticket Granting Ticket (TGT) encrypted with krbtgt account key
    3. User presents TGT to request service-specific ticket (TGS)
    4. TGS encrypted with service's NTLM hash, delivered to user
    5. User presents TGS to access the requested service
- **Security Benefit**: Decouples credentials from resource requests

![image](/images/What-Is-Kerberos-TR.jpg)

### 2. DNS (Domain Name System)

- **Role in AD**:
    - Enables clients to locate Domain Controllers
    - Facilitates DC-to-DC communication
    - Resolves hostnames to IP addresses
    - Uses port 53 (UDP primarily, TCP for large packets)
- **Key Components**:
    - Service records (SRV) help locate critical services
    - Dynamic DNS automatically updates IP changes
    - Essential for domain communication
- **Lookup Examples**:
    - Forward lookup: Find IP from domain name
    - Reverse lookup: Find hostname from IP

![image](/images/domain.jpg)

### 3. LDAP (Lightweight Directory Access Protocol)

- **Basics**:
    - Used for directory lookups and authentication
    - Operates on port 389 (LDAPS on 636)
    - Cross-platform, open-source protocol
    - Latest spec is Version 3 (RFC 4511)
- **Authentication Methods**:
    1. Simple Authentication: Username/password BIND requests
    2. SASL Authentication: Uses external services (like Kerberos)
- **Security Note**: Default LDAP messages are in cleartext - TLS recommended

![image](/images/what-is-LDAP-authentication-for-Active-Directory.png)

### 4. MSRPC (Microsoft Remote Procedure Call)

- **Key Interfaces**:
    - **lsarpc**: Manages local security policy
    - **netlogon**: Authenticates users and services
    - **samr**: Manages domain account database (attackers use for reconnaissance)
    - **drsuapi**: Handles directory replication (can be exploited to extract password hashes)

![image](/images/msrpc.png)


## Security Implications

- Domain Controllers can be identified by scanning for port 88
- LDAP authentication requires encryption to prevent credential theft
- MSRPC interfaces, especially samr and drsuapi, are frequent attack vectors
- Proper protocol configuration is essential for AD security

## Pentesting Relevance

- BloodHound leverages these protocols for AD mapping
- NTDS.dit extraction exploits drsuapi functionality
- Default permissions often allow excessive information gathering