# 📊 Domain 4 — Manage & Monitor Security Posture

**Exam weight: 20–25%**  
**Exam:** SC-500 — Cloud and AI Security Engineer Associate

---

## 📋 What This Domain Covers

This is your security control room — where you see everything, detect threats, and respond. Microsoft Defender for Cloud and Microsoft Sentinel are the two headline tools here.

### Key Topics

**Microsoft Defender for Cloud**
- Secure Score — understanding recommendations and remediation
- Defender plans — Defender for Servers, SQL, Storage, Containers, etc.
- Regulatory compliance dashboard (MCSB, NIST, PCI-DSS, ISO 27001)
- Security alerts & incidents
- Vulnerability assessments

**Microsoft Sentinel**
- Workspace design & data connectors
- Analytics rules — scheduled, NRT, fusion
- KQL (Kusto Query Language) — hunting queries and detection logic
- Incidents & investigation graph
- Playbooks (Logic Apps) — automated response
- Automation rules
- Workbooks — dashboards & visualisation

**Microsoft Purview**
- Data Security Posture Management (DSPM)
- Information protection & sensitivity labels
- Audit & compliance

**Microsoft Security Copilot**
- Workspaces & roles
- Plugins & Microsoft agents
- Security Store agents
- Integrating Copilot into security workflows

---

## 🧪 Labs

| Lab | Description | Status |
|-----|-------------|--------|
| Configured | Enable Defender for Cloud on subscription | ✅ |
| Coming soon | Sentinel — connect data sources + create analytics rule | ⏳ |
| Coming soon | Write a KQL detection query | ⏳ |
| Coming soon | Build a Sentinel playbook for automated response | ⏳ |

---

## 📚 Microsoft Learn Modules

Follow the official learning path on [Microsoft Learn](https://learn.microsoft.com/en-us/credentials/certifications/cloud-and-ai-security-engineer-associate/).

---

## 💡 Key Exam Tips

- **Defender for Cloud** = posture management + threat protection (identifies risk, recommends remediation)
- **Sentinel** = SIEM + SOAR (collect signals, correlate incidents, investigate, automate response)
- **KQL fluency is non-negotiable** — you won't need to write queries from scratch but must read and choose the correct one
- Defender plans are **per resource type** — you can enable Defender for Servers without enabling Defender for SQL
- **Playbooks** respond to incidents via automation rules — know the Logic Apps connection
