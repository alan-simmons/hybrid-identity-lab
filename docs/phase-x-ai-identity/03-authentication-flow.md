
---

# 🧱 03-authentication-flow.md

```md
# OAuth 2.0 Client Credentials Flow

## 🔐 Overview

This lab uses the **client credentials flow**, which enables machine-to-machine authentication without user interaction.

## 🔄 Flow

1. Application sends:
   - Client ID
   - Client Secret

2. Entra ID validates credentials

3. Entra returns:
   - Access token (JWT)

4. Application uses token to access resources

## 🧠 Key Insight
No user is involved.

This is used by:
- APIs
- Automation
- AI agents

## 🔥 Real-World Relevance
This is the standard authentication model for:
- Backend services
- Cloud workloads
- AI integrations
