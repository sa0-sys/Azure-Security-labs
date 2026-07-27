# Address Space

## Overview

This document defines the IP addressing strategy for the Northgate University Azure environment.

The addressing scheme is designed to:

- Support future expansion without readdressing
- Separate workloads into security zones
- Follow Azure networking best practices
- Reserve space for future hub-and-spoke networking
- Keep addressing simple and predictable

---

# Virtual Network

| Property | Value |
|----------|------|
| Name | vnet-northgate-prod |
| Address Space | 10.10.0.0/16 |
| Region | UK South |

The `/16` address space provides 65,536 private IP addresses, which is significantly more than the lab requires today. This intentionally mirrors enterprise design practices by allowing room for future workloads, additional subnets, and network expansion without changing the VNet's address space.

---

# Subnet Allocation

| Subnet | CIDR | Purpose |
|---------|------|---------|
| Management | 10.10.1.0/24 | Administrative VMs and management resources |
| Identity | 10.10.2.0/24 | Identity-related services |
| Application | 10.10.3.0/24 | Application workloads |
| Database | 10.10.4.0/24 | Database services |
| Private Endpoints | 10.10.5.0/24 | Azure Private Endpoints |
| AzureBastionSubnet | 10.10.6.0/26 | Reserved subnet for Azure Bastion |
| Reserved | 10.10.7.0/24 - 10.10.255.0/24 | Future expansion |

---

# Addressing Principles

The following principles are used throughout the environment:

- One subnet per workload or security boundary.
- Resources with different security requirements are isolated into separate subnets.
- Azure-managed services that require dedicated subnets (such as Azure Bastion) receive their own reserved subnet.
- Private Endpoints are deployed into a dedicated subnet to simplify management and security.
- Additional subnets will be created from the remaining address space as new workloads are introduced.

---

# Future Expansion

The remaining address space is reserved for future services, including:

| Planned Service | Notes |
|-----------------|------|
| Hub Virtual Network | Future AZ-700 networking labs |
| Shared Services | DNS, monitoring, management |
| Development Environment | Separate workload isolation |
| Production Environment | Future production simulation |
| VPN Gateway | If site-to-site connectivity is introduced |
| Azure Firewall | Dedicated AzureFirewallSubnet |

---

# Reserved Azure Subnets

Some Azure services require specifically named subnets.

| Service | Required Subnet |
|----------|-----------------|
| Azure Bastion | AzureBastionSubnet |
| Azure Firewall | AzureFirewallSubnet *(future)* |
| VPN Gateway | GatewaySubnet *(future)* |

These names are reserved and should not be repurposed.

---

# Address Allocation Summary

| Range | Status |
|---------|--------|
| 10.10.0.0/16 | Allocated to Northgate VNet |
| 10.10.1.0/24 | Management |
| 10.10.2.0/24 | Identity |
| 10.10.3.0/24 | Applications |
| 10.10.4.0/24 | Databases |
| 10.10.5.0/24 | Private Endpoints |
| 10.10.6.0/26 | Azure Bastion |
| Remaining | Reserved for future expansion |
