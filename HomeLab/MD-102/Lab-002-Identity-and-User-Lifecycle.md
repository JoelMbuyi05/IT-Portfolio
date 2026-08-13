# Lab 002 — Identity and User Lifecycle Management

**Date:** 13 August 2026
**Duration:** [actual time spent]
**Day:** 02 of 30-day MD-102 plan

---

## Goal

Practice managing user identities and Microsoft 365 licenses using both the Microsoft 365 admin center and PowerShell with Microsoft Graph.

The goal was to understand how users are created, viewed and managed in Microsoft Entra ID and how licenses are assigned to users.

---

## Environment

* Microsoft 365 E5 trial tenant
* Microsoft 365 admin center
* Microsoft Entra ID
* Windows 11
* PowerShell
* Microsoft Graph PowerShell SDK

---

## Steps I Took

### Part 1 — Microsoft 365 Admin Center

1. Signed into the Microsoft 365 admin center using my tenant administrator account.

2. Navigated to the user management section.

3. Opened the list of active users.

4. Reviewed the existing users in the tenant.

5. Created a test user in the Microsoft 365 admin center.

6. Entered the user's basic information.

7. Created the account and confirmed that the user appeared in the user list.

8. Opened the new user's account.

9. Reviewed the user's account information and available management options.

10. Reviewed the user's license settings.

11. Assigned an available Microsoft 365 license to the test user.

12. Confirmed that the license was successfully assigned.

13. Reviewed the user's account properties and access information.

---

### Part 2 — Microsoft Entra ID

14. Opened the Microsoft Entra admin center.

15. Navigated to **Identity → Users**.

16. Reviewed the users stored in Microsoft Entra ID.

17. Opened a user account and reviewed its properties.

18. Checked information such as the user's display name, User Principal Name and account status.

19. Confirmed that the user created through the Microsoft 365 administration environment was also available in Entra ID.

---

### Part 3 — Microsoft Graph PowerShell

20. Opened PowerShell.

21. Installed the Microsoft Graph PowerShell SDK:

```powershell
Install-Module Microsoft.Graph -Scope CurrentUser -Force
```

22. Imported the authentication module:

```powershell
Import-Module Microsoft.Graph.Authentication
```

23. Connected PowerShell to Microsoft Graph using the required permissions:

```powershell
Connect-MgGraph -Scopes "User.ReadWrite.All","Directory.ReadWrite.All" -UseDeviceAuthentication
```

24. Checked the current Graph connection:

```powershell
Get-MgContext
```

25. Listed the first 10 users:

```powershell
Get-MgUser -Top 10
```

26. Listed all users:

```powershell
Get-MgUser -All
```

27. Displayed useful properties for all users:

```powershell
Get-MgUser -All | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

28. Retrieved information about the Microsoft 365 organisation:

```powershell
Get-MgOrganization | Select-Object DisplayName,Id
```

29. Checked which Microsoft Graph modules were installed:

```powershell
Get-InstalledModule Microsoft.Graph*
```

30. Compared the information displayed in PowerShell with the information visible in the Microsoft 365/Entra admin portals.

---

## Commands Used

```powershell
Install-Module Microsoft.Graph -Scope CurrentUser -Force

Import-Module Microsoft.Graph.Authentication

Connect-MgGraph -Scopes "User.ReadWrite.All","Directory.ReadWrite.All" -UseDeviceAuthentication

Get-MgContext

Get-MgUser -Top 10

Get-MgUser -All

Get-MgUser -All | Select-Object DisplayName,UserPrincipalName,AccountEnabled

Get-MgOrganization | Select-Object DisplayName,Id

Get-InstalledModule Microsoft.Graph*
```

---

## What Broke

[Document anything that actually went wrong.]

If nothing significant went wrong:

**No major errors occurred. The main learning point was understanding how the Microsoft 365 admin center, Microsoft Entra ID and Microsoft Graph PowerShell interact with the same tenant.**

---

## How I Fixed It

[Document the actual problem and solution if something went wrong.]

If nothing broke:

**No troubleshooting was required for this lab.**

---

## Screenshots

Save screenshots of:

* Microsoft 365 admin center → Active users
* The test user's account
* The user's assigned license
* Microsoft Entra ID → Users
* PowerShell `Get-MgContext`
* PowerShell `Get-MgUser`
* PowerShell user properties
* `Get-MgOrganization`
* Installed Microsoft Graph modules

Screenshot folder:

```text
HomeLab/screenshots/Day-02/
```

---

## Lessons Learned

I learned that Microsoft Entra ID is the identity system behind the users in my Microsoft 365 tenant.

I can manage users through the graphical administration portals, but I can also use PowerShell and Microsoft Graph to retrieve and manage the same tenant information.

I also learned that creating a user and assigning a license are separate tasks. The account provides the identity, while the license determines which Microsoft 365 services the user can access.

Using PowerShell becomes especially useful when managing many users because repetitive administrative tasks can be automated.

---

## Exam Connection

This lab connects to Microsoft 365 and device administration because identity is the foundation for controlling access to Microsoft services and devices.

For MD-102 preparation, I need to understand:

* Microsoft Entra ID
* Users
* Groups
* Licenses
* User lifecycle
* Account status
* Microsoft Graph
* Graph PowerShell
* Permissions and scopes

I also need to understand how identity management connects with device management and Intune.

---

## Real Job Connection

In a real IT support environment, I may receive requests such as:

> "A new employee has started and needs Microsoft 365 access."

I would need to create or verify the user's account, assign the correct license and make sure the user has the required access.

I may also receive:

> "An employee has left the company."

I would then need to follow the organisation's offboarding process, which could include disabling the account, removing access, handling licenses and preserving required data.

If the company has many users, PowerShell and Microsoft Graph can help automate repetitive user-management tasks.

This lab gave me practical experience with the same concepts through both the GUI and command line.
