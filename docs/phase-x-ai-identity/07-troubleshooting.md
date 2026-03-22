# Troubleshooting

## Issue 1 — Used Secret ID Instead of Secret Value

Problem:
Authentication failed

Cause:
Used Secret ID instead of Secret VALUE

Fix:
- Created new client secret
- Used correct value

---

## Issue 2 — Sign-In Logs Not Visible

Problem:
No logs appeared during testing

Cause:
- Log delay
- Possible tenant limitations

Fix:
- Waited for log propagation
- Used token response as validation

---

## 🧠 Key Lesson
Authentication success can be verified through:
- Token issuance
- API responses

Logs are not always immediate
