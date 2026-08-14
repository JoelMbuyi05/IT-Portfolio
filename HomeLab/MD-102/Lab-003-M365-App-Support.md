# Lab 003 — Microsoft 365 Apps and Support

**Date:** 14 August 2026
**Day:** 03 of 30-day MD-102 plan

---

## Goal

Use the users created during the previous identity and user lifecycle lab to practice Microsoft 365 workloads and understand how licensing, mailboxes, permissions and membership affect user access.

---

## Environment

* Microsoft 365 E5 trial tenant
* Microsoft 365 admin center
* Exchange admin center
* Microsoft Entra ID
* SharePoint
* Microsoft Teams
* Outlook on the web
* Windows 11
* Private/Incognito browser

---

# Task 1 — Exchange Online

### Steps I Took

1. Signed into the Microsoft 365 administration environment using my administrator account.

2. Opened the Exchange admin center.

3. Navigated to **Recipients → Mailboxes**.

4. Located the user **alice.it**.

5. Opened Alice's mailbox information.

6. Verified that Alice had an Exchange Online mailbox.

7. Opened a private browser window.

8. Signed in as Alice.

9. Opened Outlook on the web.

10. Confirmed that Alice could access her mailbox.

11. Tested email access by sending/receiving a test message.

### Result

Alice had an Exchange Online mailbox and was able to access Outlook on the web while her Microsoft 365 license was assigned.

---

# Task 2 — SharePoint

### Steps I Took

1. Opened the SharePoint administration environment.

2. Created a new team site called:

**IT Department**

3. Added:

* `emma.it`
* `iris.it`

as members.

4. Opened the site and verified that the IT users could access it.

5. Opened a private browser window.

6. Signed in as:

**bob.hr**

7. Attempted to access the **IT Department** SharePoint site.

8. Checked the result and used the access behavior to understand how SharePoint membership and permissions control access.

### Result

The test demonstrated that SharePoint access is controlled by site permissions and membership rather than simply by whether a user exists in the tenant.

---

# Task 3 — Microsoft Teams

### Steps I Took

1. Opened Microsoft Teams.

2. Created a new team called:

**XYZ-IT-Team**

3. Added the IT users to the team.

4. Signed in as an IT user using a private browser session.

5. Verified that the user could see and access the team.

6. Tested access using a user who was not intended to be part of the IT team.

### Result

The IT users could access the team because they were members of the team.

This demonstrated how Teams membership controls access to a team's collaboration environment.

---

# Task 4 — License Removal

### Steps I Took

1. Confirmed that Alice could access Outlook before changing her license.

2. Opened Alice's account in the administration environment.

3. Removed her Microsoft 365 license.

4. Waited for the licensing change to propagate.

5. Opened a private browser.

6. Attempted to access Outlook on the web as Alice.

7. Observed the effect of removing the license.

8. Reassigned Alice's Microsoft 365 license.

9. Waited for the change to propagate.

10. Tested Outlook access again.

11. Confirmed that access was restored after the license was reassigned.

### Result

Removing the Microsoft 365 license affected Alice's access to the licensed Microsoft 365 services, while her underlying Entra identity remained present.

Reassigning the license restored the relevant service access after the change propagated.

---

## Commands Used

No PowerShell commands were required for this lab.

The lab was primarily performed through:

* Microsoft 365 admin center
* Exchange admin center
* SharePoint
* Microsoft Teams
* Outlook on the web
* Microsoft Entra ID

---

## What Broke


**Nothing significant broke during the lab. The main troubleshooting exercise was intentionally removing Alice's license and observing the resulting change in Microsoft 365 service access.**

---

## How I Fixed It

The license was intentionally removed as part of the test.

I reassigned Alice's Microsoft 365 license and waited for the change to propagate. I then tested Outlook again and confirmed that the relevant access was restored.

---


## Lessons Learned

I learned how the different Microsoft 365 workloads connect to the identity and licensing system I studied previously.

A user needs an identity in Entra ID, the appropriate license for the services they need, and the correct permissions or membership for specific resources.

I also learned that troubleshooting access should be systematic.

For example:

**User cannot access Outlook**

→ Check identity
→ Check account status
→ Check license
→ Check Exchange mailbox
→ Check service availability
→ Test Outlook on the web

For SharePoint and Teams:

**User cannot access resource**

→ Check identity
→ Check license
→ Check membership
→ Check permissions
→ Test access again

---

## Exam Connection

This lab connects identity management with Microsoft 365 workload administration.

I practiced:

* Exchange Online mailboxes
* Outlook access
* SharePoint sites
* SharePoint permissions
* Microsoft Teams
* Teams membership
* Microsoft 365 licensing
* User access troubleshooting

The important concept is that **identity, licensing and permissions work together to determine what a user can access.**

---

## Real Job Connection

In a real IT support role, users may report:

> "I can't access my email."

> "I can't access the department SharePoint site."

> "The Teams team disappeared."

> "I used to have access but now I don't."

Instead of immediately changing the user's password or reinstalling software, I can investigate the user's identity, license, mailbox, group/team membership and permissions.

This lab gave me practical experience troubleshooting access from the administrator side.
