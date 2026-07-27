# Northgate University Azure Environment

This directory documents the architecture used throughout the Azure Security Labs.

Rather than deploying isolated resources, every lab contributes to a single enterprise environment that evolves.

The environment follows Microsoft Cloud Adoption Framework recommendations while remaining cost-effective enough to run within an Azure Free Trial subscription.

```mermaid
flowchart TB

    Users((Users))

    Internet((Internet))

    AGW[Application Gateway]

    Users --> Internet
    Internet --> AGW

    subgraph Azure["Azure Subscription"]

        subgraph RG["Resource Group: rg-network-prod"]

            subgraph VNET["Virtual Network: vnet-northgate-prod
            10.10.0.0/16"]

                MGMT["Management
                10.10.1.0/24"]

                ID["Identity
                10.10.2.0/24"]

                APP["Application
                10.10.3.0/24"]

                DB["Database
                10.10.4.0/24"]

                PE["Private Endpoints
                10.10.5.0/24"]

                BAS["AzureBastionSubnet
                10.10.6.0/26"]

            end
        end

        KV[Azure Key Vault]

        ST[Storage Account]

    end

    APP --> KV
    APP --> ST
    PE --> KV
    PE --> ST
```
