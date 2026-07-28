# Northgate University Azure Environment

This directory documents the architecture used throughout the Azure Security Labs.

Rather than deploying isolated resources, every lab contributes to a single, evolving enterprise environment.

The environment adheres to Microsoft Cloud Adoption Framework recommendations while remaining cost-effective enough to run on an Azure Free Trial subscription.

# Current Architecture

> Last Updated: 27 July 2026

## High-Level Architecture

```text
                    Internet
                        │
                Application Gateway
                        │
────────────────────────────────────────────
           Northgate Virtual Network
              10.10.0.0/16
────────────────────────────────────────────
│
├── Management Subnet
│
├── Identity Subnet
│
├── Application Subnet
│
├── Database Subnet
│
└── Private Endpoint Subnet
```

---

## Current Resources

### Networking

| Resource | Name | Status |
|----------|------|--------|
| Virtual Network | vnet-northgate | Configured |
| NSG | nsg-management | Configured |
| Route Table | rt-northgate | Configured |

### Identity

| Resource | Name | Status |
|----------|------|--------|
| Microsoft Entra ID | Default Tenant | Configured |
| Conditional Access | Baseline Policies | Configured |

### Security

| Resource | Name | Status |
|----------|------|--------|
| Key Vault | kv-northgate-prod | Configured |
| Storage Account | - | Planned |
| Private Endpoint | prep-keyvault | Configured |

---

## Current Network Flow

```text
Internet
↓
Application Gateway
↓
Application Subnet
↓
Database Subnet

Administrators
↓
Azure Bastion
↓
Management Subnet

Applications
↓
Private Endpoint
↓
Key Vault

```
---

## Planned Changes

- Configure NSGs
- Deploy Storage Account
