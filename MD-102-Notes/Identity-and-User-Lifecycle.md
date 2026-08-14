# Day 02 — Identity and User Lifecycle

**Date:** 13 August 2026
**Source:** Microsoft Learn

---

## What I Learned Today

Today I learned how identity and user lifecycle management works in Microsoft Entra ID.

Microsoft Entra ID is Microsoft's cloud identity and access management service. It stores and manages users, groups, devices and other identities that are used to access Microsoft cloud services.

I learned how to create and manage users through the Microsoft 365 admin center and through PowerShell.

I also learned how licenses are assigned to users. A user can exist in Entra ID without having a Microsoft 365 license, but the license determines which Microsoft 365 services and features that user can use.

I practiced using Microsoft Graph PowerShell to connect to my tenant and retrieve information about users and the organisation.

This showed me that many tasks that can be performed through the graphical admin center can also be automated using PowerShell and Microsoft Graph.

---

## Key Concepts

* **Microsoft Entra ID** = Microsoft's cloud identity and access management service.
* **User lifecycle** = creating, managing, updating, disabling and eventually removing user accounts.
* **License** = determines which Microsoft 365 services and features are available to a user.
* **Microsoft Graph** = Microsoft's API platform for accessing and managing Microsoft 365 and Entra resources.
* **Microsoft Graph PowerShell SDK** = PowerShell commands that interact with Microsoft Graph.
* **User Principal Name (UPN)** = the sign-in name used by a user, usually in an email-style format.
* **AccountEnabled** = indicates whether a user account is enabled.
* **Scopes/permissions** = determine what actions a connected application or PowerShell session is allowed to perform.

---

## Commands I Used

### Install Microsoft Graph PowerShell

```powershell
Install-Module Microsoft.Graph -Scope CurrentUser -Force
```

### Load the authentication module

```powershell
Import-Module Microsoft.Graph.Authentication
```

### Connect to Microsoft Graph

```powershell
Connect-MgGraph -Scopes "User.ReadWrite.All","Directory.ReadWrite.All" -UseDeviceAuthentication
```

### Check the current Graph connection

```powershell
Get-MgContext
```

### List the first 10 users

```powershell
Get-MgUser -Top 10
```

### List all users

```powershell
Get-MgUser -All
```

### Display useful user properties

```powershell
Get-MgUser -All | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### Get tenant/organisation information

```powershell
Get-MgOrganization | Select-Object DisplayName,Id
```

### Check installed Microsoft Graph modules

```powershell
Get-InstalledModule Microsoft.Graph*
```

---

## What Confused Me

At first I thought Microsoft Graph was another administration portal. I now understand that Microsoft Graph is an API that allows applications and tools such as PowerShell to interact with Microsoft 365 and Entra resources.

I also had to understand the difference between creating a user and licensing a user. Creating the account gives the user an identity in Entra ID, while assigning a license gives the user access to the Microsoft 365 services included in that license.

---

## How This Connects to the Job

User lifecycle management is a common IT administration task.

When a new employee joins a company, IT may need to:

1. Create the user's account.
2. Assign the appropriate license.
3. Add the user to the correct groups.
4. Configure access.
5. Provide the user with their sign-in information.

When an employee leaves, IT may need to disable the account, remove access and eventually remove or retain the account according to company policy.

PowerShell and Microsoft Graph are especially useful when many users need to be managed because repetitive tasks can be automated instead of being performed manually through the admin portal.

---

## Exam Tips

* Know what Microsoft Entra ID is used for.
* Understand the difference between an identity and a Microsoft 365 license.
* Know that Microsoft Graph provides programmatic access to Microsoft 365 and Entra resources.
* Understand that Graph PowerShell cmdlets can be used to manage users and other resources.
* Understand that permissions/scopes control what Graph operations are allowed.
* Know common user properties such as `DisplayName`, `UserPrincipalName` and `AccountEnabled`.
* Remember that disabling a user is different from deleting the user.

---

## Defend Question

Question: A new employee starts Monday. Walk me through creating their account and getting them access to Microsoft 365.

Answer:
First, I would confirm the employee's details and what access they need, including their department, role and required Microsoft 365 license. Then I would create the user account in Microsoft Entra ID or the Microsoft 365 admin center, using the correct UPN and account information. I would assign the appropriate Microsoft 365 license, add the user to the required groups, and verify that the account is enabled. Finally, I would confirm the user can sign in and access the services they need. If there are many new employees, I could use Microsoft Graph PowerShell to automate the repetitive parts of the process.

## Wrong Answers From Practice Questions

**Q:** [Paste the question you got wrong]

**Correct answer:** [Answer]

**Why I got it wrong:** [Your honest reason]

**What I now know:** [Correct understanding]
