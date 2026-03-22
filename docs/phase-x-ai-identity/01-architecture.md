# Architecture — AI Agent Identity Flow

## 🔄 Authentication Flow

AI Agent → Entra ID → Access Token → Resource

## 🧱 Flow Breakdown

1. AI agent sends:
   - Client ID
   - Client Secret
   - Tenant ID

2. Microsoft Entra ID validates identity

3. Entra issues access token (JWT)

4. AI uses token to access resource

## 🧩 Components

| Component | Purpose |
|----------|--------|
| App Registration | Defines AI identity |
| Service Principal | Identity instance in tenant |
| Client Secret | Authentication credential |
| Access Token | Authorization to access resources |
| Resource (API) | Target system |

## 🧠 Conceptual Resource
AI-Lab-File-API:
- Read files
- List files
- No write/delete access
