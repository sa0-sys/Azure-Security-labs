# Naming Convention

## Overview

This document defines the naming standards used throughout the Northgate University Azure environment.

The objectives of this convention are to:

- Keep resource names consistent and predictable.
- Make resources easy to identify.
- Follow common Azure naming practices.
- Support future growth without renaming resources.

---

# General Format

Most Azure resources follow this pattern:

```
<resource-type>-<workload>-<environment>
```

Example:

```
vnet-northgate-prod
```

Where:

| Component | Description | Example |
|-----------|-------------|---------|
| Resource Type | Azure resource abbreviation | `vnet` |
| Workload | Application or project name | `northgate` |
| Environment | Deployment environment | `prod` |

---

# Environment Codes

| Environment | Code |
|-------------|------|
| Production | `prod` |
| Development | `dev` |
| Test | `test` |
| Lab | `lab` |

Although this project is a personal learning environment, the `prod` suffix is used to simulate a production deployment for Northgate University.

---

# Resource Naming Standards

| Resource | Format | Example |
|----------|--------|---------|
| Resource Group | `rg-<workload>-<purpose>` | `rg-northgate-network` |
| Virtual Network | `vnet-<workload>-<environment>` | `vnet-northgate-prod` |
| Subnet | `<purpose>-subnet` | `management-subnet` |
| Network Security Group | `nsg-<purpose>` | `nsg-management` |
| Route Table | `rt-<purpose>` | `rt-private-endpoints` |
| Storage Account | `st<workload><environment>` | `st-northgate-prod` |
| Key Vault | `kv-<workload>-<environment>` | `kv-northgate-prod` |
| Virtual Machine | `vm-<role>-<environment>` | `vm-management-prod` |
| Managed Identity | `mi-<workload>-<purpose>` | `mi-webapp` |
| Private Endpoint | `pep-<resource>` | `pep-keyvault` |
| Private DNS Zone | `pdns-<service>` | `pdns-keyvault` |
| Public IP | `pip-<resource>` | `pip-appgateway` |
| Application Gateway | `agw-<workload>-<environment>` | `agw-northgate-prod` |
| Log Analytics Workspace | `law-<workload>` | `law-northgate` |
| Recovery Services Vault | `rsv-<workload>` | `rsv-northgate` |

---

# Naming Principles

The following principles apply to all resources:

- Use lowercase letters.
- Separate words with hyphens where supported.
- Keep names short but descriptive.
- Avoid spaces and special characters.
- Use singular nouns.
- Keep names consistent across all resource types.

---

# Azure Naming Exceptions

Some Azure resources have platform-specific naming requirements.

## Storage Accounts

Storage account names:

- Must be globally unique.
- Can only contain lowercase letters and numbers.
- Cannot contain hyphens.
- Must be between 3 and 24 characters.

Example:

```
stnorthgateprod
```

---

## Key Vault

Key Vault names:

- Must be globally unique.
- Support lowercase letters, numbers, and hyphens.

Example:

```
kv-northgate-prod
```

---

# Future Resources

The following naming patterns will be used as additional services are introduced.

| Resource | Example |
|----------|---------|
| Azure Firewall | `afw-northgate-prod` |
| VPN Gateway | `vpngw-northgate` |
| Bastion | `bas-northgate` |
| Azure DNS Resolver | `dnsr-northgate` |
| Virtual WAN | `vwan-northgate` |

---

# Example Deployment

```
rg-northgate-network
│
├── vnet-northgate-prod
│
├── management-subnet
├── identity-subnet
├── application-subnet
├── database-subnet
│
├── nsg-management
├── nsg-identity
├── nsg-application
│
├── kv-northgate-prod
├── st-northgate-prod
└── prep-keyvault
```
