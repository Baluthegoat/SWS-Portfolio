---
title: "Active Directory"
description: "Active Directory Groups"
pubDate: 2025-04-30
heroImage: "/Types-of-Active-Directory-security-groups.png"
readingTime: "5 min read"
tags: ["Notes", "Active Directory"]
---


## Active Directory Groups

- **Purpose of Groups:**
    
    Groups in Active Directory (AD) are used to organize users, computers, 
    and contacts to simplify management of permissions and resource access. 
    Instead of assigning permissions individually, admins assign rights to 
    groups, and all members inherit those permissions.
    
- **Groups vs Organizational Units (OUs):**
    - **Groups:** Primarily for assigning permissions to resources.
    - **OUs:** Used for organizing objects for
    management and applying Group Policy, and delegating administrative
    tasks without granting broad rights.
- **Group Types:**
    - **Security Groups:** Used to assign permissions to resources (files, printers, shares). Members inherit these permissions.
    - **Distribution Groups:** Used for email distribution lists (e.g., Microsoft Exchange). Cannot be used for permission assignments.
- **Group Scopes:**
    1. **Domain Local Groups:**
        - Used to assign permissions to resources within the same domain.
        - Can contain users from any domain but cannot be used across domains.
        - Can be nested within other domain local groups but not global groups.
    2. **Global Groups:**
        - Can only contain users from their own domain.
        - Can be used to assign permissions in any domain within the forest.
        - Can be nested within other global or domain local groups.
    3. **Universal Groups:**
        - Can contain users from any domain in the forest.
        - Used to assign permissions across multiple domains.
        - Stored in the Global Catalog (GC), causing forest-wide replication on membership changes.
        - Best practice: Nest global groups inside universal groups to minimize replication overhead.
- **Built-in vs Custom Groups:**
    - AD comes with many built-in groups (e.g., Domain Admins, Enterprise Admins) with predefined scopes and privileges.
    - Built-in groups generally do not allow group nesting; only user accounts can be members.
    - Organizations create custom groups for specific access needs.
    - Adding applications like Exchange creates additional groups, some with high privileges.
- **Nested Group Membership:**
    - Groups can be members of other groups, allowing users to inherit permissions indirectly.
    - This can lead to unintended privilege escalation if not carefully managed.
    - Tools like BloodHound help visualize and analyze nested group memberships and privilege inheritance.
- **Important Group Attributes:**
    - **cn:** Common name of the group.
    - **member:** Users, groups, or contacts that belong to the group.
    - **groupType:** Indicates group type and scope.
    - **memberOf:** Groups that contain this group as a member (nested membership).
    - **objectSid:** Unique security identifier for the group.
- **Group Scope Conversion Rules:**
    - Global groups can be converted to Universal if not members of other global groups.
    - Domain Local groups can be converted to Universal if they don’t contain other Domain Local groups.
    - Universal groups can be converted to Domain Local without restrictions.
    - Universal groups can be converted to Global only if they don’t contain other Universal groups.

## Summary

Active Directory groups are essential for managing permissions and access efficiently within an enterprise environment.  They allow administrators to assign rights to collections of users and resources, greatly simplifying access control and auditing. Understanding the differences between group types (security vs distribution) and scopes (domain local, global, universal) is critical for proper group management and security. Mismanagement of groups, especially nested groups, can 
lead to unintended privilege escalation and security risks. Regular auditing of group memberships and privileges is necessary to prevent excessive or inappropriate access. Tools like BloodHound provide valuable insights into complex group nesting and privilege inheritance.

Built-in groups provide foundational roles with predefined privileges, while custom groups allow organizations to tailor access control to their specific needs. Proper use and understanding of AD groups help maintain a secure and manageable Active Directory environment.