# Secure Access to Resources by Using Microsoft Entra

**Learning path:** [Secure access to resources by using Microsoft Entra](https://learn.microsoft.com/en-us/training/paths/secure-access-resources-entra/)
**Environment:** Northgate University (tenant: `northgateunigmail.onmicrosoft.com`)
**Status:** In progress
**Entra ID P2 trial activated:** 2026-07-22

---

## How to use this manual

This file is the fixed lab plan — it doesn't change as you go. It covers every
module and unit in the learning path, mapped to a Northgate build task.

Your workflow:
1. Read a unit on Microsoft Learn.
2. Come back here, find the matching lab step, and build it in the Northgate tenant.
3. Check the box.
4. Commit. Small and often beats one big commit at the end.

The checkboxes here track *build* progress. `README.md` (separate file) is the polished summary you update every so often.

---

## Northgate scenario for this lab

Northgate's IT Security team needs to close three related gaps:
- Weak, inconsistent MFA enrollment across staff and students
- Standing (permanent) admin privileges with no expiry or approval trail
- An unsecured API integration behind a new Microsoft 365 Copilot declarative
  agent being piloted by the Registrar's office

Each module below tackles one piece of that.

---

## Module 1 — Manage and implement authentication methods

**Northgate goal:** every Northgate user has a modern, enforced authentication
story — from first factor to password reset — with registration itself locked down.

| # | Unit | Lab task | Done |
|---|---|---|---|
| 1.1 | [Introduction](https://learn.microsoft.com/en-us/training/modules/manage-implement-authentication-methods/1-introduction) | Read only — no build | ✅ |
| 1.2 | [Explore authentication methods](https://learn.microsoft.com/en-us/training/modules/manage-implement-authentication-methods/2-explore-authentication-methods) | In Entra admin center, review current Authentication methods policy for Northgate tenant. Note which methods are enabled by default. | ✅ |
| 1.3 | [Configure MFA](https://learn.microsoft.com/en-us/training/modules/manage-implement-authentication-methods/3-configure-mfa) | Build: (a) CA policy requiring MFA for all users, (b) a named location for a "trusted" Northgate IP range, (c) CA policy restricting the `Register security information` action to trusted location or TAP, (d) a registration campaign with an enrollment deadline | ✅ |
| 1.4 | [Implement passwordless authentication](https://learn.microsoft.com/en-us/training/modules/manage-implement-authentication-methods/4-implement-passwordless-authentication) | Enable at least one passwordless method (e.g. Authenticator passwordless sign-in or passkeys) in the Authentication methods policy for a pilot group (e.g. IT staff) | ✅ |
| 1.5 | [Configure SSPR](https://learn.microsoft.com/en-us/training/modules/manage-implement-authentication-methods/5-configure-self-service-password-reset) | Enable SSPR for a Northgate user group, configure required authentication methods for reset | ✅ |
| 1.6 | [Exercise: Configure authentication methods](https://learn.microsoft.com/en-us/training/modules/manage-implement-authentication-methods/6-exercise-configure-authentication-methods) | Follow the official guided exercise directly against Northgate instead of a throwaway sandbox | ✅ |
| 1.7 | [Module assessment](https://learn.microsoft.com/en-us/training/modules/manage-implement-authentication-methods/7-knowledge-check) | Complete — no build | ✅ |
| 1.8 | [Summary](https://learn.microsoft.com/en-us/training/modules/manage-implement-authentication-methods/8-summary) | Read only | ✅ |

**Verification for Module 1:** sign in as a test user and confirm MFA is
challenged; attempt to register security info from an "untrusted" location and
confirm it's blocked or requires TAP; trigger SSPR as a test user.

---

## Module 2 — Implement and configure Privileged Identity Management (PIM)

**Northgate goal:** remove standing admin access; key staff (e.g. IT Security
lead, Registrar admin) get time-bound, approval-gated privilege instead.

| # | Unit | Lab task | Done |
|---|---|---|---|
| 2.1 | [Introduction](https://learn.microsoft.com/en-my/training/modules/implement-configure-privileged-identity-management/1-introduction) | Read only | ✅ |
| 2.2 | [Why PIM and JIT access matter](https://learn.microsoft.com/en-my/training/modules/implement-configure-privileged-identity-management/2-explain-privileged-just-in-time-access) | Read only — write a short note on which existing tenant-wide role assignments (from your Northgate setup) should become PIM-eligible instead of permanent | ✅ |
| 2.3 | [Core capabilities of PIM](https://learn.microsoft.com/en-my/training/modules/implement-configure-privileged-identity-management/3-explore-privileged-identity-features) | In Entra admin center, open PIM and review available settings (activation duration, MFA-on-activation, approval, justification) | ✅ |
| 2.4 | [JIT access for Microsoft Entra roles](https://learn.microsoft.com/en-my/training/modules/implement-configure-privileged-identity-management/4-implement-just-in-time-entra-roles) | Convert at least one existing permanent Entra role assignment (e.g. a staff member's admin role) to PIM-eligible; configure activation settings (max duration, require MFA, require justification) | ✅ |
| 2.5 | [JIT access for Azure roles/resources](https://learn.microsoft.com/en-my/training/modules/implement-configure-privileged-identity-management/5-implement-just-in-time-azure-roles-resources) | Assign a PIM-eligible Azure RBAC role (e.g. Contributor) on a resource group in the Northgate subscription | ✅ |
| 2.6 | [Scaling with PIM for Groups](https://learn.microsoft.com/en-my/training/modules/implement-configure-privileged-identity-management/6-explore-privileged-access-groups) | Create a PIM-for-Groups scenario: an existing Northgate security group becomes eligible-membership instead of standing membership | ✅ |
| 2.7 | [JIT for AI workloads, agents, applications](https://learn.microsoft.com/en-my/training/modules/implement-configure-privileged-identity-management/7-apply-privilege-workloads-agents-apps) | Read + design note: how would JIT apply to the Registrar's declarative agent (module 3)? Document the approach, even if not fully built | ✅ |
| 2.8 | [JIT design patterns and best practices](https://learn.microsoft.com/en-my/training/modules/implement-configure-privileged-identity-management/8-review-design-patterns) | Read only — capture 3–5 best practices as notes | ✅ |
| 2.9 | [Module assessment](https://learn.microsoft.com/en-my/training/modules/implement-configure-privileged-identity-management/9-knowledge-check) | Complete — no build | ✅ |
| 2.10 | [Summary](https://learn.microsoft.com/en-my/training/modules/implement-configure-privileged-identity-management/10-summary) | Read only | ✅ |

**Verification for Module 2:** Activate an eligible role as the test admin,
confirm MFA/justification prompt, confirm the activation appears in PIM audit
history with a clear start/end time.

---

## Module 3 — Authenticate your API plugin for declarative agents with secured APIs

**Different environment note:** this module needs VS Code, Node.js v20, the
Microsoft 365 Agents Toolkit extension, Azure Functions Tools, and an M365
tenant with Copilot — not just the Entra admin center. Budget separate setup
time before starting unit 3.1.

**Northgate goal:** the Registrar's pilot declarative agent authenticates to
its backend API securely — first with an API key, then hardened to OAuth2.

| # | Unit | Lab task | Done |
|---|---|---|---|
| 3.1 | Introduction | Read only; confirm dev environment (VS Code, Node.js v20, Agents Toolkit, Azure Functions Tools) is installed | ✅ |
| 3.2 | Integrate an API plugin with an API secured with a key | Build a minimal Azure Function API secured with an API key; wire it into a declarative agent's API plugin | ✅ |
| 3.3 | Exercise — API key integration | Follow guided exercise against your own Northgate-themed API (e.g. "Registrar lookup" stub) | ✅ |
| 3.4 | Integrate an API plugin with an API secured with OAuth2 | Reconfigure the same API to require OAuth2; update the plugin auth config accordingly | ✅ |
| 3.5 | Exercise — OAuth2 integration | Follow guided exercise; validate the agent authenticates via OAuth2 instead of a static key | ✅ |
| 3.6 | Module assessment | Complete — no build | ✅ |
| 3.7 | Summary | Read only | ✅ |

**Verification for Module 3:** run the declarative agent in Microsoft 365
Copilot, confirm it successfully calls the API under both auth methods (at
different points), and document why OAuth2 is the stronger end-state (ties
back to module 2's JIT-for-agents note in 2.7).
