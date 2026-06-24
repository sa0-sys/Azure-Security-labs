# 🌐 Domain 2 — Secure Storage, Databases & Networking

**Exam weight: 25–30%**  
**Exam:** SC-500 — Cloud and AI Security Engineer Associate

---

## 📋 What This Domain Covers

The largest domain by weight. Think of this as securing the walls, pipes, and vaults of your Azure environment — everything data flows through or rests in.

### Key Topics

**Networking**
- Network Security Groups (NSGs) & Application Security Groups (ASGs)
- Azure Firewall & Firewall Manager
- Azure DDoS Protection
- Private Endpoints & Private Link
- Azure Front Door & Application Gateway WAF
- Azure Bastion — secure RDP/SSH without public IPs
- VPN Gateway & ExpressRoute security

**Storage**
- Storage account firewalls & virtual network rules
- Shared Access Signatures (SAS tokens)
- Customer-Managed Keys (CMK) & encryption
- Immutability policies & soft delete
- Microsoft Defender for Storage

**Databases**
- Azure SQL — Transparent Data Encryption (TDE), Always Encrypted, Dynamic Data Masking
- Microsoft Defender for SQL
- Azure Cosmos DB security
- Private endpoints for data services

---

## 🧪 Labs

| Lab | Description | Status |
|-----|-------------|--------|
| Coming soon | Deploy NSG with custom inbound/outbound rules | ⏳ |
| Coming soon | Configure Azure Firewall + WAF on App Gateway | ⏳ |
| Coming soon | Storage account — private endpoint + CMK | ⏳ |
| Coming soon | Azure SQL — enable TDE + Dynamic Data Masking | ⏳ |

---

## 📚 Microsoft Learn Modules

Follow the official learning path on [Microsoft Learn](https://learn.microsoft.com/en-us/credentials/certifications/cloud-and-ai-security-engineer-associate/).

---

## 💡 Key Exam Tips

- Know when to use **NSG vs Azure Firewall vs WAF** — each operates at a different layer
- **Private Endpoints** bind a service to your VNet with a private IP — eliminating public internet exposure
- **Always Encrypted** protects data from DBAs; **TDE** protects data at rest; **Dynamic Data Masking** limits exposure to non-privileged users — know the difference
- **SAS tokens** vs **managed identities** — prefer managed identities for app-to-service auth
