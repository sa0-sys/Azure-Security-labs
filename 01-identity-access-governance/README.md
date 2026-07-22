# 🔐 Domain 1 — Manage Identity, Access & Governance

**Exam weight:** 20–25%
**Exam:** SC-500 — Cloud and AI Security Engineer Associate

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

## 🧪 Labs

| Lab | Description | Status |
|---|---|---|
| [Secure access to resources by using Microsoft Entra](secure-access-entra/) | MFA + Conditional Access, passwordless auth, SSPR, PIM just-in-time access (Entra roles, Azure roles, PIM for Groups, AI agents), and declarative agent API plugin auth (API key & OAuth2) | 🔄 In progress |
| Azure Key Vault — defense in depth | Access policies vs RBAC, secrets, keys, certificates | ⏳ Coming soon |
| Azure Policy & governance | Policy definitions, initiatives, enforce tagging & allowed regions, regulatory compliance | ⏳ Coming soon |

## 📚 Microsoft Learn Modules

Follow the official learning path on Microsoft Learn:
- [Secure access to resources by using Microsoft Entra](https://learn.microsoft.com/en-us/training/paths/secure-access-resources-entra/)
- [Secure Azure Key Vault with defense in depth for the cloud and AI workloads](https://learn.microsoft.com/en-us/training/paths/configure-key-vault-security/)
- [Enforce security governance and regulatory compliance](https://learn.microsoft.com/en-us/training/paths/security-governance-compliance/)

## 💡 Key Exam Tips

- Know the difference between Azure RBAC roles (resource-level) and Entra directory roles (tenant-level) — they are separate systems
- PIM eligible = must activate with MFA/approval; PIM active = always active
- Conditional Access is preventive (evaluated at token issuance); Entra ID Protection is reactive (responds to detected risk)
- Key Vault access policies vs RBAC — know when to use each
- Registration itself is a high-value target: a compromised password can be used to register a rogue MFA method if the `Register security information` action isn't gated by Conditional Access
