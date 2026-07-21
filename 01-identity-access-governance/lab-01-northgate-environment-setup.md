# Lab 01 — Building the Northgate University Identity Foundation
 
**Domain:** Identity & Access Governance  
**Module:** Manage Security Controls for Identity and Access (SC-500)  
**Difficulty:** Beginner  
**License Required:** Entra ID Free  
**Date Completed:** July 2026
 
---
 
## Overview
 
As part of my SC-500 exam preparation, I decided to build a fictional university environment — **Northgate University** — to ground the abstract identity concepts in something realistic. Rather than working through isolated exercises, I wanted a scenario that felt like a real organisation with real security problems to solve.
 
Northgate University is a mid-sized research university with four faculties:
 
- 🏗️ Faculty of Engineering & Technology
- ⚕️ Faculty of Medicine & Health Sciences
- ⚖️ Faculty of Law & Social Sciences
- 🔬 Faculty of Research & Innovation
In this lab, I built the identity foundation of Northgate's Microsoft Entra ID tenant from scratch — provisioning users, organising them into security groups, creating Administrative Units per faculty, and assigning tenant-wide roles to key staff.
 
---
 
## Environment
 
- **Tenant:** `northgateunigmail.onmicrosoft.com`
- **License:** Microsoft Entra ID Free
- **Portal:** Microsoft Entra admin centre / Azure portal

---

## What I Did
 
### Part 1 — Bulk Importing Student Users
 
The first thing I needed was users. Rather than creating accounts one by one, I used Entra ID's **bulk create** feature, which accepts a CSV file and provisions multiple users in one operation. This is how large organisations typically handle user provisioning at scale.
 
I prepared a CSV file with 40 student accounts — 10 per faculty — covering all the required fields from Microsoft's official bulk create template including display name, username (UPN), initial password, department, and usage location.
 
To do this I navigated to:
 
**Microsoft Entra ID → Users → Bulk operations → Bulk create**
 
I uploaded the CSV and monitored the import via **Bulk operation results**. 

> 📸 *Bulk operation results showing 40 successful student imports*
<img width="3024" height="834" alt="Screenshot 2026-07-21 120540" src="https://github.com/user-attachments/assets/9a4353f2-af37-49f1-ab64-f501fa307168" />

> 📸 *All users list filtered by Engineering department confirming student accounts*
<img width="2457" height="1800" alt="Screenshot 2026-07-21 120919" src="https://github.com/user-attachments/assets/2d9f240f-966c-467d-b78b-d09df7e1c0fc" />

All 40 accounts were created successfully across the four faculties.

---

### Part 2 — Bulk Importing Staff Users
 
I followed the same process for staff accounts — 26 users covering IT admins, academic staff, administrative staff, and one external collaborator (Erik Nilsson, Visiting Researcher).
 
Two accounts failed during import due to **username conflicts** with existing student accounts:
 
| Failed Username | Conflict With | Resolution |
|---|---|---|
| `h.forsythe@...` | Student Harriet Forsythe | Recreated manually as `helen.forsythe@...` |
| `r.kingsley@...` | Student Rose Kingsley | Recreated manually as `robert.kingsley@...` |
 
This was a useful reminder that username conventions need to be planned carefully at scale — a conflict like this in a real environment could delay onboarding.
 
> 📸 *Manual user creation form for Helen Forsythe*
<img width="1848" height="1161" alt="Screenshot 2026-07-21 123220" src="https://github.com/user-attachments/assets/e4e6d996-3348-4000-8dcf-b741b137fcd6" />

 
**Note on Erik Nilsson:** Erik was provisioned as a regular member account for lab purposes. In a real deployment, an external collaborator like Erik would be onboarded through the **Entra B2B invitation flow** — an invitation would be sent to his institutional email (e.g. `e.nilsson@stockholmuni.se`), which he would accept to link his external identity to Northgate's tenant as a guest. This isn't possible to simulate without a real external email address, so I've documented the correct approach here for reference. The B2B guest flow will be covered properly in a future lab.
 
---


### Part 3 — Creating Security Groups
 
With users in place, I created security groups to organise them by faculty and function. The purpose of these groups is to control **resource access** — what systems, apps, and data each set of users can reach.
 
I navigated to:
 
**Microsoft Entra ID → Groups → New group**
 
Each group was created as a **Security group** with **Assigned** membership type.
 
**Student groups created:**
 
| Group Name | Purpose |
|---|---|
| `GRP-Students-Engineering` | Access to Engineering student resources |
| `GRP-Students-Medicine` | Access to Medicine student resources |
| `GRP-Students-Law` | Access to Law student resources |
| `GRP-Students-Research` | Access to Research student resources |
| `GRP-All-Students` | Tenant-wide student communications and shared access |
 
**Staff groups created:**
 
| Group Name | Purpose |
|---|---|
| `GRP-IT-Admins` | IT administration access |
| `GRP-Engineering-Staff` | Engineering faculty systems access |
| `GRP-Medicine-Staff` | Medicine faculty systems access |
| `GRP-Law-Staff` | Law faculty systems access |
| `GRP-Research-Staff` | Sensitive research systems access |
| `GRP-HR-Finance` | HR and Finance systems access |
| `GRP-Admin-Staff` | General administrative systems access |
| `GRP-External-Collaborators` | Restricted guest access |
| `GRP-All-Staff` | Tenant-wide staff communications and shared access |


> 📸 *Completed groups list in Microsoft Entra ID*
<img width="2607" height="1728" alt="Screenshot 2026-07-21 121414" src="https://github.com/user-attachments/assets/fd2c3fc0-7139-4fdf-8638-888fb0d0c743" />


One thing I learned here is the distinction between **security groups** and **Microsoft 365 groups** — security groups are for resource access control. In contrast, M365 groups create collaboration spaces like Teams and SharePoint sites. For this lab, I focused on security groups as the access control foundation.

---


### Part 4 — Creating Administrative Units
 
This was the most conceptually interesting part of the lab. Administrative Units (AUs) are different from groups — while groups control what resources users can access, AUs control **which users an admin can manage**. They create a management boundary rather than an access boundary.
 
The problem I was solving here is realistic: without AUs, a Faculty IT Admin like Liam Chen would have tenant-wide user management permissions — meaning he could technically reset passwords or modify accounts for Medicine or Law students, which is a clear least-privilege violation.
 
I created four AUs, one per faculty, and added the relevant staff and students as members:
 
| AU | Faculty IT Admin | Members |
|---|---|---|
| `AU-Engineering` | Liam Chen | Engineering staff + 10 Engineering students |
| `AU-Medicine` | Amara Nwosu | Medicine staff + 10 Medicine students |
| `AU-Law` | Priya Sharma | Law staff + 10 Law students |
| `AU-Research` | Daniel Osei | Research staff + 10 Research students + Erik Nilsson |
 
I navigated to:
 
**Microsoft Entra ID → Roles and admins → Admin Units → + Add**
 
After creating each AU, I added members via:
 
**AU → Members → + Add members**

> 📸 *AU-Engineering members list showing staff and students*
<img width="2994" height="1707" alt="Screenshot 2026-07-21 121934" src="https://github.com/user-attachments/assets/e99ecaf7-d70d-4145-9955-24395e1fb315" />

> 📸 *All four Administrative Units created in Entra ID*
<img width="2787" height="876" alt="Screenshot 2026-07-21 121859" src="https://github.com/user-attachments/assets/12d1d435-f47d-4336-8e7a-2e26199e4a23" />


**Known Limitation:** Assigning roles scoped to an Administrative Unit requires **Microsoft Entra ID P2**. I deliberately deferred activating the P2 trial to preserve the 30-day window for later labs covering PIM, Identity Protection, and Conditional Access — where P2 is more heavily used. The AUs are fully built and ready; scoped role assignments will be completed in a follow-up lab.
 
---
 
The final step was assigning built-in Entra ID roles to key staff members at the tenant level. This enforces least privilege — each person gets only the permissions their role genuinely requires.
 
I navigated to:
 
**Microsoft Entra ID → Roles and administrators**
 
Then clicked each role → **+ Add assignments** → searched for the user → **Assign**.
 
| User | Role Assigned | Justification |
|---|---|---|
| James Okafor | Global Reader | IT Director needs tenant-wide visibility without the ability to make changes |
| Bernard Walsh | Security Reader | Security Analyst monitors security signals across the tenant |
| Victor Nwachukwu | Helpdesk Administrator | Systems Admin handles password resets and basic user support |
| Sandra Eze | User Administrator | HR Manager manages the staff account lifecycle |
| Helen Forsythe | Compliance Administrator | Compliance Officer needs access to compliance centre tools |


> 📸 *Role assignment for James Okafor as Global Reader*
<img width="3078" height="927" alt="Screenshot 2026-07-21 122322" src="https://github.com/user-attachments/assets/2bb7678f-23cf-47ce-9701-5e97ee2980e7" />


## What I Learned
 
- **Bulk import is the realistic approach** for user provisioning at scale. Manual creation is useful for understanding the fields involved, but in any organisation with more than a handful of users, CSV bulk operations or scripted provisioning via Microsoft Graph is the standard approach.
- **Username conflicts are a real operational concern.** Having a naming convention that accounts for common name clashes (e.g. using full first names rather than initials) would have avoided the two failures I hit during staff import.
- **Groups and Administrative Units serve different purposes** and both are needed in a well-structured tenant. Groups = access boundaries. AUs = management boundaries.
- **P2 licensing is a genuine constraint** in enterprise environments. Features like scoped role assignment within AUs, PIM, and Identity Protection all sit behind the P2 license — understanding which features require it is important for both exam and real-world planning.
- **Least privilege starts at the role assignment level.** Giving James Okafor Global Reader instead of Global Administrator is a deliberate security decision — he needs visibility, not control.

---

## Lab Files
 
| File | Description |
|---|---|
| `northgate_students_bulk_import.csv` | 40 student accounts across all four faculties |
| `northgate_staff_bulk_import.csv` | 26 staff accounts across IT, academic, admin, and external |
 
---
 
## References
 
- [Microsoft Entra ID Overview](https://learn.microsoft.com/en-us/entra/fundamentals/whatis)
- [Bulk create users in Entra ID](https://learn.microsoft.com/en-us/entra/identity/users/users-bulk-add)
- [Administrative Units in Entra ID](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/administrative-units)
- [Entra ID Built-in Roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference)
 
