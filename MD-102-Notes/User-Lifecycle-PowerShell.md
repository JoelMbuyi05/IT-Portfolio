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

If an interviewer asks:

"How would you onboard a new employee in Microsoft 365?"

A strong short answer would be:

"I'd create the user's Entra ID account, configure the required attributes and UPN, assign the appropriate license, verify the account, and then make sure the user can receive the required device and security policies through Intune."

## Wrong Answers From Practice Questions

1. What problem does Microsoft Entra ID solve?
Answer: It manages user identities, authentication, and access to Microsoft/cloud resources.

2. What is a UPN?
Answer: The user's sign-in name, usually formatted like an email address.

3. Is a UPN necessarily the same as an email address?
Answer: No. They can be the same, but they serve different purposes.

4. What is the purpose of the .onmicrosoft.com domain?
Answer: It's the default domain created with a Microsoft 365 tenant and can be used for user identities.

5. What's the difference between creating one user manually and bulk provisioning users?
Answer: Manual creation is suitable for a few users; bulk provisioning automates creating many users.

6. Why would an administrator use PowerShell/Microsoft Graph?
Answer: To automate and efficiently manage users and other Microsoft resources at scale.

7. What does assigning a license accomplish?
Answer: It gives the user access to the services and features included in that license.

8. Why can a user exist in Entra but still not have access to a particular service?
Answer: Because the user may not have the required license, permissions, or access policy.

9. How would you verify that a user was successfully created?
Answer: Check the user in the Entra admin center or query the account using Microsoft Graph/PowerShell.

10. If a user can't access something they should have access to, what are the first things you'd investigate?
Answer: Check the user's account status, license, permissions, and applicable access policies.
