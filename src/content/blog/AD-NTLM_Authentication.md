---
title: "Active Directory"
description: "NTML Authentication"
pubDate: 2025-04-30
heroImage: "/guide-ntlm-authentication2.png"
readingTime: "5 min read"
tags: ["Notes", "Active Directory"]
---

## NTLM Authentication

- Active Directory (AD) supports multiple authentication methods: LM, NTLM, NTLMv1, NTLMv2, Kerberos, and LDAP.
- Kerberos is generally preferred for security, but NTLM
and its variants are still widely used and can be abused in AD
environments.

**Hash and Protocol Comparison**

| Hash/Protocol | Cryptography | Mutual Authentication | Message Type | Trusted Third Party |
| --- | --- | --- | --- | --- |
| LM | Symmetric (DES) | No | Random number | Domain Controller |
| NTLM/NTLMv1 | Symmetric (MD4) | No | Random number | Domain Controller |
| NTLMv2 | Symmetric (MD4, HMAC-MD5) | No | Random number | Domain Controller |
| Kerberos | Symmetric & Asymmetric | Yes | Encrypted ticket | Domain Controller/KDC |

**LM Hashes**

- Oldest and weakest; introduced in 1987.
- Passwords limited to 14 characters, not case sensitive, converted to uppercase.
- Hashing splits password into two 7-character chunks, each encrypted with DES.
- Easy to crack with modern tools due to limited keyspace and algorithm weaknesses.
- Disabled by default since Windows Vista/Server 2008, but may still be present in legacy environments.

**NTLM Hashes (NTHash)**

- Used in modern Windows systems.
- Challenge-response protocol: NEGOTIATE_MESSAGE, CHALLENGE_MESSAGE, AUTHENTICATE_MESSAGE.
- NT hash is MD4(UTF-16-LE(password)).
- More secure than LM, supports full Unicode character set.
- Still vulnerable to brute-force attacks and "pass-the-hash" attacks, where the hash can be used directly for authentication if obtained


**NTLMv1 (Net-NTLMv1)**

- Uses both NT and LM hashes.
- Challenge/response mechanism: server sends 8-byte challenge, client responds with 24-byte response.
- Susceptible to offline cracking and relay attacks.
- Cannot be used for pass-the-hash attacks.

**NTLMv2 (Net-NTLMv2)**

- Default since Windows Server 2000.
- Stronger than NTLMv1; uses HMAC-MD5 and includes client/server challenges, timestamps, and domain name in the response.
- More resistant to spoofing and replay attacks, but still not as robust as Kerberos

**Domain Cached Credentials (MSCache2)**

- Allows authentication when a domain controller is unreachable.
- Stores last ten domain user hashes locally.
- Hashes are slow to crack and cannot be used for pass-the-hash attacks.
- Useful for offline authentication but a potential target if an attacker gains local admin rights

**Security Implications**

- LM and NTLM hashes are weak and should be disabled where possible.
- NTLM and its variants remain vulnerable to several attack vectors, including brute-force, pass-the-hash, and relay attacks.
- Kerberos is preferred for environments requiring strong authentication and mutual verification.

**Summary Table: Hash/Protocol Features**

| Feature | LM | NTLM/NTLMv1 | NTLMv2 | Kerberos |
| --- | --- | --- | --- | --- |
| Password Length Limit | 14 chars | None | None | None |
| Case Sensitivity | No | Yes | Yes | Yes |
| Salt Used | No | No | No | Yes |
| Mutual Authentication | No | No | No | Yes |
| Pass-the-Hash Attack | Yes | Yes | No | No |
| Default in Modern AD | No | No | Yes | Yes |


- Understanding the differences, weaknesses, and attack vectors of each authentication method is crucial for securing AD environments and conducting effective penetration testing