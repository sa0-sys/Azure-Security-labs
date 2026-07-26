# Learning Path 1: Secure Access to Resources by Using Microsoft Entra

**Status:** In progress
**Learning path:** [Secure access to resources by using Microsoft Entra](https://learn.microsoft.com/en-us/training/paths/secure-access-resources-entra/)
**Environment:** Northgate University (tenant: `northgateunigmail.onmicrosoft.com`)
**Lab manual:** [MANUAL.md](./MANUAL.md)

## Scenario

Northgate's IT Security team needs to close three related gaps: weak/inconsistent
MFA enrollment, standing admin privileges with no expiry, and an unsecured API
integration for a new Microsoft 365 Copilot declarative agent being piloted by
the Registrar's office.

## Modules covered

| Module | Status |
|---|---|
| 1. Manage and implement authentication methods | ✅ Completed |
| 2. Implement and configure Privileged Identity Management (PIM) | ✅ Completed | 
| 3. Authenticate your API plugin for declarative agents with secured APIs | 🔄 In progress | 

## Setup notes

- Entra ID P2 trial activated on 2026-07-22 to support Conditional Access
  registration controls (Module 1) and PIM (Module 2).
- Module 3 requires a separate dev environment: VS Code, Node.js v20, Microsoft
  365 Agents Toolkit extension, Azure Functions Tools.

## Build log

The full task-by-task plan lives in [MANUAL.md](./MANUAL.md).
