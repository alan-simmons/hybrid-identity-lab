# Monitoring and Logging

## 🔍 Sign-In Logs

Location:
- Entra ID → Monitoring & health → Sign-in logs
- Enterprise Applications → Sign-in logs

## ⚠️ Lab Observation

Service principal sign-in logs were delayed and did not appear during the test window.

## ✅ Sign-In Log Validation

A successful service principal sign-in was captured.

This confirms:
- Authentication flow executed correctly
- Token request was processed by Entra ID
- Activity is logged and traceable

## 🔐 Security Insight
Even non-human identities (AI, apps, automation) generate sign-in logs and should be monitored just like user accounts.

## ✅ Validation Method

Authentication was confirmed through:
- Successful OAuth token response
- Correct execution of client credentials flow

## 🧠 Key Insight
Token issuance confirms successful authentication, even if logs are delayed.

## 🔥 Security Principle
AI identities must be monitored just like user accounts.
