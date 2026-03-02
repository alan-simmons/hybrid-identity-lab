# 06 – Group Policy & Tier Governance Implementation

## 🎯 Objective

Implement enterprise-grade identity governance using:

- Central Store
- Baseline Workstation GPO
- Tier Enforcement GPO
- Domain Controller Logon Restrictions
- Advanced Audit Policy

This phase transitions the lab from **“AD deployed”** to **“AD governed.”**

---

# Phase 1 – Central Store Implementation

## Purpose

Standardize ADMX templates across Domain Controllers to ensure consistent GPO editing and eliminate template mismatch warnings.

## Implementation

Central Store path:

```
\\corp.local\SYSVOL\corp.local\Policies\PolicyDefinitions
```

PowerShell validation:

```powershell
$domain = (Get-ADDomain).DNSRoot
$centralStore = "\\$domain\SYSVOL\$domain\Policies\PolicyDefinitions"
New-Item -Path $centralStore -ItemType Directory -Force
```

Copy ADMX templates:

```powershell
robocopy C:\Windows\PolicyDefinitions \\corp.local\SYSVOL\corp.local\Policies\PolicyDefinitions /MIR
```

## Validation

- `Test-Path` confirmed SYSVOL path
- `repadmin /replsummary` returned 0 errors
- No ADMX mismatch warnings in GPMC

---

# Phase 2 – Tier 2 Baseline Workstation GPO

## GPO Name

T2 – Workstation Baseline

## Linked To

```
OU=Standard,OU=Workstations,OU=Corp
```

## Configured Settings

- UAC Enabled
- Windows Defender Enabled
- Windows Firewall Enabled
- SMB Signing Required
- Basic Audit Policy (Logon, Account Logon, Policy Change, Privilege Use)

## Validation (CL01)

```cmd
gpupdate /force
gpresult /r
```

Confirmed applied GPO:

- T2 – Workstation Baseline

---

# Phase 3 – Tier Enforcement GPO (Prevent Downward Logon)

## GPO Name

T2 – Tier Enforcement

## Linked To

```
OU=Workstations
```

## Path

```
Computer Configuration
 → Policies
   → Windows Settings
     → Security Settings
       → User Rights Assignment
```

## Configured

### Deny log on locally

- GG_T0_Admins
- GG_T1_Server_Admins

### Deny log on through RDP

- GG_T0_Admins
- GG_T1_Server_Admins

## Validation

Attempted Tier 1 login on CL01.

Result:

> “The sign-in method you're trying to use isn't allowed.”

Tier isolation confirmed.

---

# Phase 4 – Domain Controller Logon Restriction (Tier 0 Protection)

## GPO Name

T0 – DC Logon Restriction

## Linked To

```
OU=Domain Controllers
```

## Configured

### Deny log on locally

- Domain_Users
- GG_T1_Server_Admins
- GG_T2_Helpdesk

### Deny log on through RDP

- Everyone except GG_T0_Admins

No explicit “Allow log on locally” was defined to avoid overriding defaults.

## Validation

- Tier 1 login to DC → Blocked
- Tier 2 login to DC → Blocked
- Tier 0 login to DC → Successful

Tier boundary enforced.

---

# Phase 5 – Advanced Audit Policy

## GPO Name

T0 – Advanced Audit Policy

## Linked To

```
OU=Domain Controllers
```

## Enabled Subcategories

### Account Logon

- Kerberos Authentication Service (Success, Failure)
- Kerberos Service Ticket Operations (Success, Failure)

### Logon/Logoff

- Logon (Success, Failure)
- Special Logon (Success)

### Account Management

- User Account Management (Success, Failure)
- Security Group Management (Success, Failure)

### DS Access

- Directory Service Changes (Success, Failure)

## Validation

```powershell
auditpol /get /category:* | findstr Success
```

Confirmed configured subcategories enabled.

---

# Authentication Correlation Validation

User: Helpdesk.T2  
Client: CL01 (192.168.1.135)

Observed sequence:

1. Event 4768 – TGT Issued  
2. Event 4769 – Service Ticket Requested  
3. Event 4624 – Network Logon (Type 3)  
4. Event 4672 – Privileged Session (if applicable)

This confirms:

- Kerberos auditing functional
- Client IP traceable
- AES encryption visible
- Tier enforcement active
- Privileged logon detection possible

---

# Governance Checklist

- Central Store replicated
- Multi-DC replication healthy
- Tier 2 baseline applied
- Tier enforcement working
- DC restricted to Tier 0
- Advanced audit logging enabled
- Kerberos event visibility confirmed

---

# Lab Status

Active Directory is:

- Hardened
- Governed
- Observable
- Tier-enforced
- Audit-validated

Environment maturity level: Enterprise-aligned.
