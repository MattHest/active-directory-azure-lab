# Active Directory Deployment in Azure

## Overview
In this project I built a basic Active Directory environment in Microsoft Azure using a Windows Server domain controller and a Windows 10 client. The goal was to simulate a small business setup with centralized user management and security policies.

## Environment Setup
I created a virtual network in Azure and deployed two virtual machines: DC-1 (Windows Server 2022) as the Domain Controller and Client-1 (Windows 10) as a domain client. The domain controller was assigned a static private IP, and the client machine was configured to use it for DNS.

## Active Directory Configuration
I installed Active Directory Domain Services on DC-1 and promoted it to a Domain Controller. The domain mydomain.com was created, and I set up Organizational Units for _EMPLOYEES, _ADMINS, and _CLIENTS. User accounts were created and placed into the appropriate OUs, including an admin account added to the Domain Admins group.

## Client Domain Join
Client-1 was joined to the domain and tested using domain credentials to confirm authentication was working properly across the environment.

## Group Policy Configuration
I configured an account lockout policy through Group Policy with a threshold of 5 failed attempts and a 30-minute lockout/reset window to simulate basic security controls.

## Troubleshooting
During setup, I ran into a domain join issue caused by incorrect DNS settings on the client machine. After pointing DNS to the domain controller, the issue was resolved. I used tools like ipconfig, ping, and Active Directory utilities to verify connectivity and configuration.

## Screenshots
### Azure Virtual Machines
![Azure VMs](azure-vms.png)

### Active Directory Structure
![AD Users](ad-admins.png)

### Domain Join Verification
![Domain Join](domain-join.png)

### Group Policy Configuration
![Group Policy](group-policy.png)

## Key Takeaways
Active Directory depends heavily on DNS, Organizational Units help structure user management, Group Policy enforces security, and troubleshooting is a key part of deployment.
