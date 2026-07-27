# Azure Key Vault

## Overview

Azure Key Vault is Azure's managed secret management service. It provides a secure location for storing and controlling access to sensitive information used by applications and services.

Rather than embedding credentials directly in source code or configuration files, workloads retrieve them securely from Key Vault at runtime.

---

# What Key Vault Stores

Azure Key Vault stores three primary object types:

| Object | Purpose |
|---------|---------|
| Keys | Encryption and cryptographic operations |
| Secrets | Passwords, API keys, connection strings, tokens, storage account keys |
| Certificates | SSL/TLS certificates and private keys |

---

# Secrets

Secrets are stored as **Name → Value** pairs.

Example:

| Name | Value |
|------|-------|
| SqlAdminPassword | ******** |
| StorageKey | ******** |
| GraphApiToken | ******** |

Applications request a secret by its **name**.

Example:

```
Get Secret

Name:
SqlAdminPassword

↓

Returns

Actual password
```

---

# Secret Versioning

Each time a secret value changes, Azure Key Vault automatically creates a new version.

```
SqlAdminPassword

├── Version 1
│   Password123
│
├── Version 2
│   Password456
│
└── Version 3
    Password789
```

Benefits:

- Secret rotation without losing history
- Rollback if required
- Auditability

---

# Secret Attributes

Secrets can include metadata such as:

- Enabled / Disabled
- Activation date
- Expiration date
- Content type
- Tags

These attributes help with lifecycle management without changing the secret value.

---

# Secret Rotation

Secrets should be rotated regularly.

Typical workflow:

```
Old Password

↓

Create New Secret Version

↓

Update Application

↓

Disable/Delete Old Version
```

Automatic rotation reduces the risk of compromised credentials.

---

# Access Control

Microsoft recommends managing Key Vault access using **Azure RBAC** rather than legacy Key Vault Access Policies.

Typical roles include:

- Key Vault Administrator
- Key Vault Secrets Officer
- Key Vault Secrets User
- Key Vault Reader

RBAC centralizes authorization through Microsoft Entra ID.

---

# Managed Identities

Applications should authenticate using Managed Identities instead of stored credentials.

```
Application

↓

Managed Identity

↓

Azure Key Vault

↓

Retrieve Secret

↓

Use Secret
```

This removes the need to store passwords inside applications.

---

# Networking

Key Vault should be protected with multiple layers of network security.

Recommended controls:

- Private Endpoint
- Disable Public Network Access
- Firewall Rules
- Trusted Microsoft Services (where appropriate)

Applications should access Key Vault over private networking whenever possible.

---

# Security Features

Azure Key Vault includes:

- Soft Delete
- Purge Protection
- Diagnostic Logs
- Azure Monitor Integration
- Microsoft Defender for Cloud recommendations

---

# Recommended Architecture

```
                 Microsoft Entra ID
                        │
                        ▼
               Managed Identity
                        │
                        ▼
                Azure Key Vault
        ┌─────────────────────────┐
        │ Secrets                 │
        │ Keys                    │
        │ Certificates            │
        └─────────────────────────┘
                        ▲
                        │
                Private Endpoint
                        │
                        ▼
              Azure Virtual Network
                        │
        ┌───────────────┴──────────────┐
        │                              │
    App Service                  Azure Function
```

---

# Best Practices

- Never hardcode secrets in source code.
- Use Managed Identities whenever possible.
- Use Azure RBAC for authorization.
- Enable Soft Delete and Purge Protection.
- Rotate secrets regularly.
- Use Private Endpoints to eliminate public exposure.
- Monitor access with Azure Monitor and diagnostic logs.
- Apply the principle of least privilege.

---

# Key Takeaways

- Azure Key Vault is Azure's centralized secret management service.
- Secrets are stored as Name → Value pairs.
- Secret updates create new versions automatically.
- Applications should retrieve secrets dynamically rather than storing them.
- Managed Identities eliminate the need for application credentials.
- Azure RBAC is the recommended authorization model.
- Defense in depth combines identity, networking, monitoring, and data protection.
