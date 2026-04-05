# Active Directory Deployment in Azure

## Overview
In this project, I built a basic Active Directory environment using Microsoft Azure. The setup includes a Windows Server domain controller and a Windows 10 client joined to the domain.

The goal was to simulate a small business environment where users are managed centrally and security policies are applied through Group Policy.

---

## Environment Setup
I created a virtual network in Azure and deployed two virtual machines:

- DC-1 (Windows Server 2022) – Domain Controller  
- Client-1 (Windows 10) – Domain-joined workstation  

The domain controller was given a static private IP, and the client machine was configured to use it as its DNS server.

---

## Active Directory Configuration
Active Directory Domain Services (AD DS) was installed on DC-1, and the server was promoted to a Domain Controller.

I created a new domain: mydomain.com

To organize users, I set up the following Organizational Units:
- _EMPLOYEES  
- _ADMINS  
- _CLIENTS  

User accounts were created and placed into the appropriate OUs. I also added an admin account to the Domain Admins group.

---

## Client Domain Join
Client-1 was joined to the domain using domain credentials. After joining, I verified that users could log in successfully using their domain accounts.

This confirmed that DNS and domain services were working correctly.

---

## Group Policy Configuration
I configured a basic account lockout policy through Group Policy to simulate security controls:

- Lockout threshold: 5 failed attempts  
- Lockout duration: 30 minutes  
- Reset counter: 30 minutes  

This shows how policies can be enforced across all users in the domain.

---

## Troubleshooting
During the setup, I ran into an issue where the client machine could not join the domain. This ended up being caused by incorrect DNS settings.

After pointing the client’s DNS to the domain controller, the issue was resolved and the join worked as expected.

I used the following tools to verify and troubleshoot:
- `ipconfig /all`  
- `ping`  
- Active Directory Users and Computers  

---

## Screenshots

### Azure Virtual Machines
![Azure VMs](azure-vms.png)

### Active Directory Structure
![AD Users](ad-admins.png)

### Domain Join Verification
![Domain Join](domain-join.png)

### Group Policy Configuration
![Group Policy](group-policy.png)

---

## Key Takeaways
- Active Directory relies heavily on correct DNS configuration  
- Organizational Units help keep users structured and manageable  
- Group Policy allows centralized control over security settings  
- Troubleshooting is a big part of the process, not just setup  
