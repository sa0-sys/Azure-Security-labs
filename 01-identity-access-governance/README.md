# 🔐 Domain 1 — Manage Identity, Access & Governance

**Exam weight: 20–25%**  
**Exam:** SC-500 — Cloud and AI Security Engineer Associate

---

## 📋 What This Domain Covers

This domain is the foundation of everything else — if identity isn't secured, nothing else matters. Think of it as the front door to your Azure environment.

### Key Topics

- **Microsoft Entra ID** — Users, groups, service principals, managed identities
- **Azure RBAC** — Role assignments, custom roles, deny assignments
- **Privileged Identity Management (PIM)** — Just-in-time access, eligible vs active assignments
- **Conditional Access** — MFA, sign-in risk policies, named locations
- **Microsoft Entra ID Protection** — Risky users, risky sign-ins
- **Azure Policy** — Policy definitions, initiatives, compliance
- **Microsoft Entra Permissions Management** — Cloud infrastructure entitlement management
- **Azure Key Vault** — Access policies vs RBAC, secrets, keys, certificates

---

## 🧪 Labs

| Lab | Description | Status |
|-----|-------------|--------|
| Coming soon | PIM — configure eligible role assignments | ⏳ |
| Coming soon | Conditional Access — build a MFA policy | ⏳ |
| Coming soon | Azure Policy — enforce tagging & allowed regions | ⏳ |
| Coming soon | Key Vault — deploy with RBAC & soft delete | ⏳ |

---

## 📚 Microsoft Learn Modules

Follow the official learning path on [Microsoft Learn](https://learn.microsoft.com/en-us/credentials/certifications/cloud-and-ai-security-engineer-associate/).

---

## 💡 Key Exam Tips

- Know the difference between **Azure RBAC roles** (resource-level) and **Entra directory roles** (tenant-level) — they are separate systems
- **PIM eligible** = must activate with MFA/approval; **PIM active** = always active
- **Conditional Access** is *preventive* (evaluated at token issuance); **Entra ID Protection** is *reactive* (responds to detected risk)
- **Key Vault access policies vs RBAC** — know when to use each
