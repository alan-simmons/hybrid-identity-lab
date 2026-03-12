# Hybrid Identity Lab

Enterprise-style identity lab demonstrating Active Directory, hybrid identity with Microsoft Entra ID, authentication flows, and security hardening.

This project simulates a **real corporate identity environment** combining:

- Active Directory Domain Services
- DNS / Kerberos authentication
- Tiered administrative model
- Group Policy governance
- Hybrid identity with Microsoft Entra ID
- Identity synchronization and SSO
- Authentication monitoring and troubleshooting

The goal of this lab is to **develop practical IAM, system administration, and troubleshooting skills** using technologies found in modern enterprise environments.

---

                         Internet / SaaS Applications
                                   │
                                   │  SSO (SAML / OAuth / OIDC)
                                   ▼
                     Microsoft Entra ID (Identity Provider)
                     simmonsalanproton.onmicrosoft.com
                                   │
                                   │  Entra Connect (Phase 9)
                                   ▼
                      Active Directory Domain — corp.local
                                   │
                 ┌─────────────────┴─────────────────┐
                 │                                   │
            Domain Controllers                   File Services
           ├── DC01 (Core)                      └── FS01
           └── DC02 (GUI)                          │
                                                    │
                                               Client Access
                                               └── CL01


This architecture demonstrates both:

• **Traditional enterprise identity (Active Directory)**  
• **Modern cloud identity (Microsoft Entra ID)**

---

# Key Skills Demonstrated

### Identity & Authentication
- Active Directory Domain Services
- Kerberos authentication flow
- NTLM fallback analysis
- DNS SRV records and DC locator
- Authentication logs and troubleshooting

### Identity Governance
- Role Based Access Control (RBAC)
- AGDLP group design
- Tiered administrative model
- Least privilege access design

### Security Hardening
- Admin tier isolation
- Authentication policies
- NTLM monitoring
- Group Policy governance

### Hybrid Identity
- Microsoft Entra ID tenant
- Cloud identity objects
- Identity provider architecture
- Preparation for Entra Connect synchronization

---

# Lab Documentation

Detailed labs are located in the `/docs` folder.

| Phase | Topic |
|------|------|
| 01 | Active Directory Deployment |
| 02 | DNS & Kerberos Authentication |
| 03 | Identity Governance (AGDLP) |
| 04 | Tiered Administrative Model |
| 05 | DC Locator & DNS Behavior |
| 06 | Group Policy & Security Controls |
| 07 | Identity Hardening |
| 08 | Microsoft Entra ID Tenant Setup |
| 09 | Hybrid Identity with Entra Connect |
| 10 | SSO and Federation |

---

# Example Lab Topics

Some examples of the hands-on labs included:

- Troubleshooting DNS and authentication failures
- Kerberos ticket inspection
- Domain Controller discovery process
- Tiered admin account design
- Role-based access control using security groups
- Identity synchronization between AD and Entra
- Monitoring authentication events

---

# Technologies Used

- Windows Server 2022
- Active Directory Domain Services
- Microsoft Entra ID
- DNS / Kerberos
- Group Policy
- PowerShell
- Proxmox virtualization

---

# Purpose of This Project

This lab was built to:

- Develop **real-world IT troubleshooting skills**
- Understand **enterprise identity architecture**
- Practice **security-focused identity design**
- Document hands-on learning for professional development

---

# Author

Alan Simmons

Certifications:

- CompTIA A+
- CompTIA Network+
- CompTIA Security+
- CompTIA Linux+
- Ethical Hacking Essentials (EHE)

LinkedIn:  
https://www.linkedin.com/in/simmonsalan/



