# Day 03 — Microsoft 365 Apps and Support

**Date:** 14 August 2026
**Source:** Microsoft Learn

---

## What I Learned Today

Today I learned how the identity and licensing work I did previously connects to the actual Microsoft 365 services users work with.

I practiced with Exchange Online, SharePoint, Microsoft Teams and OneDrive.

I learned that creating a user in Entra ID does not automatically mean that the user can access every Microsoft 365 service. The user's license and the permissions configured for each service also affect what they can access.

I verified that a licensed user such as Alice can have an Exchange Online mailbox and access Outlook on the web.

I also learned that SharePoint and Teams use membership and permissions to control access to collaboration resources.

Finally, I tested what happens when a user's Microsoft 365 license is removed. The user's Entra identity still exists, but access to services provided by the license can be affected.

---

## Key Concepts

* **Exchange Online** = Microsoft's cloud-based email and mailbox service.
* **Mailbox** = the user's Exchange Online mailbox used for email, calendar and related functionality.
* **SharePoint** = Microsoft 365's platform for collaboration, document management and sites.
* **SharePoint permissions** = determine who can access a site and its content.
* **Microsoft Teams** = collaboration platform for teams, channels, meetings, chat and files.
* **OneDrive** = personal work-file storage for an individual Microsoft 365 user.
* **License** = enables the Microsoft 365 services included in the assigned license.
* **Membership** = determines whether a user belongs to a particular team or collaboration group.
* **Access is layered** = a user needs the correct identity, licensing and permissions for the service they are trying to use.

---

## What I Practiced

* Verified Alice's Exchange Online mailbox.
* Signed in as Alice and tested Outlook on the web.
* Created an **IT Department** SharePoint team site.
* Added Emma and Iris as members.
* Tested access using Bob from Finance.
* Created the **XYZ-IT-Team** in Microsoft Teams.
* Added the IT users and verified their access.
* Removed Alice's Microsoft 365 license and tested the effect on Outlook access.
* Reassigned Alice's license and verified access again.

---

## What Confused Me

I initially thought that having an Entra ID account was enough to access Microsoft 365 services. I now understand that identity, licensing and service-specific permissions all work together.

I also learned that SharePoint and Teams access is not simply controlled by whether a user exists in the tenant. Membership and permissions determine whether the user can access a particular collaboration resource.

---

## How This Connects to the Job

If a user says:

> "I cannot access Outlook."

I should not immediately assume Outlook itself is broken.

I would check:

1. Is the user's Entra account enabled?
2. Does the user have the correct Microsoft 365 license?
3. Does the user have an Exchange Online mailbox?
4. Can the user authenticate successfully?
5. Is there a service or tenant issue?

If a user cannot access a SharePoint site, I would investigate their membership and the site's permissions.

If a user cannot access Teams, I would check whether they are a member of the correct team and whether their account and license are valid.

This gives me a structured troubleshooting approach instead of immediately reinstalling applications or resetting passwords.

---

## Exam Tips

* **Exchange Online → email and mailboxes**
* **SharePoint → sites, documents and collaboration**
* **Teams → teams, channels and collaboration**
* **OneDrive → individual user's work files**
* A user existing in Entra ID does not automatically mean they have access to every Microsoft 365 workload.
* Licensing determines which Microsoft 365 services are available.
* Permissions and membership determine access to specific resources.
* Removing a license does not delete the Entra user account.

---

## Defend Question 

"A user says they can't access their SharePoint site. What do you check first?"

Answer out loud: First I'd determine whether they can authenticate to Microsoft 365. Then I'd check their SharePoint permissions and licensing, and finally check Conditional Access or other policies that could be blocking access.

---

## Questions + short answers

1. What is Exchange Online?

Answer: Microsoft's cloud-based email and mailbox service.

2. What is SharePoint Online?

Answer: Microsoft's service for organizational sites, documents, and collaboration content.

3. What is Teams?

Answer: Microsoft's collaboration platform for chat, meetings, calls, and teamwork.

4. What is OneDrive?

Answer: Personal cloud storage for a user's work files.

5. Does having a Microsoft 365 license automatically give a user access to every SharePoint site?

Answer: No. They also need appropriate permissions to the site/content.

6. What is the difference between licensing and permissions?

Answer: Licensing provides entitlement to services; permissions determine what the user can access within those services.

7. A user can't access a SharePoint site. What do you check?

Answer: Check authentication, licensing, SharePoint permissions, and Conditional Access/policies.

8. A user can't access email. What do you check?

Answer: Check the account, license, mailbox, authentication, and whether the issue is Outlook or Exchange.

9. Why test Outlook on the web?

Answer: It helps determine whether the problem is with the mailbox/service or the local Outlook client.

10. Why is this relevant to endpoint administration?

Answer: Endpoint admins manage the devices users use to access these Microsoft 365 services.

