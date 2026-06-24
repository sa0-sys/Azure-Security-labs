# 💻 Domain 3 — Secure Compute

**Exam weight: 20–25%**  
**Exam:** SC-500 — Cloud and AI Security Engineer Associate

---

## 📋 What This Domain Covers

Securing the workloads themselves — VMs, containers, apps, and crucially for SC-500, **AI solutions**. This is where the new SC-500 goes beyond the old AZ-500.

### Key Topics

**Virtual Machines**
- Azure Disk Encryption & Server-Side Encryption with CMK
- Just-in-Time (JIT) VM access
- Azure Bastion for secure admin access
- Microsoft Antimalware & update management
- VM vulnerability assessments via Defender for Cloud

**Containers & Kubernetes**
- AKS network policies & RBAC
- Microsoft Defender for Containers
- Pod identity & workload identity
- Image scanning & runtime protection

**App Services & Serverless**
- Managed identities for App Service
- Key Vault references in app settings
- Access restrictions & private endpoints
- App Service TLS/SSL & certificate management

**AI Workloads (SC-500 specific)**
- Securing Azure OpenAI & AI services
- AI workload identity & access controls
- Microsoft Purview for AI data governance
- Monitoring AI solutions for security risks
- Microsoft Security Copilot — workspaces, roles, plugins

---

## 🧪 Labs

| Lab | Description | Status |
|-----|-------------|--------|
| Coming soon | Enable JIT access on a VM | ⏳ |
| Coming soon | Deploy AKS with network policies + Defender | ⏳ |
| Coming soon | App Service — managed identity + Key Vault ref | ⏳ |
| Coming soon | Secure Azure OpenAI deployment | ⏳ |

---

## 📚 Microsoft Learn Modules

Follow the official learning path on [Microsoft Learn](https://learn.microsoft.com/en-us/credentials/certifications/cloud-and-ai-security-engineer-associate/).

---

## 💡 Key Exam Tips

- **JIT access** reduces attack surface by opening VM ports only when needed, for a limited time
- **System-assigned managed identity** — tied to one resource's lifecycle; **user-assigned** — standalone, reusable across multiple resources
- **Defender for Containers** covers image scanning, runtime protection, and AKS hardening
- AI workload security is new to SC-500 — don't underestimate it; Security Copilot roles and plugins are examinable
