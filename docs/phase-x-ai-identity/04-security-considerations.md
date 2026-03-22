# Security Considerations

## ⚠️ Over-Permission Risk
If an AI identity is over-permissioned:
- Data could be modified or deleted
- Privilege abuse risk increases

## 🔒 Least Privilege Applied
AI agent was restricted to:
- Read-only access

## 🔑 Secret Exposure Risk
A client secret was exposed during testing.

Mitigation:
- Secret was deleted
- New secret should be generated
- Secrets should be stored securely (e.g., Key Vault)

## 🧠 Key Principle
AI identities should be treated like privileged accounts
