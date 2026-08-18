# Day 08 — Conditional Access

Date: 15 August 2026
Source:
- Microsoft Learn — "Implement Conditional Access"
- John Savill — "Conditional Access explained"

==================================================
WHAT I LEARNED TODAY
==================================================

Today I learned about Microsoft Entra Conditional Access.

Conditional Access allows an organisation to control access to
Microsoft 365 and other cloud resources based on conditions
around a sign-in.

I learned to think about every Conditional Access policy using
four questions:

WHO
→ Which users, groups or roles does the policy apply to?

WHAT
→ Which applications or cloud resources are being accessed?

WHEN
→ Under what conditions should the policy apply?

Examples:
- Location
- Device platform
- Sign-in risk
- Client application
- Device state

THEN
→ What should happen when the conditions are met?

Examples:
- Allow access
- Block access
- Require MFA
- Require a compliant device

A Conditional Access policy therefore follows this general
logic:

WHO + WHAT + WHEN
        ↓
      THEN

==================================================
KEY CONCEPTS
==================================================

Conditional Access
- Controls access to cloud resources based on conditions.
- Uses Microsoft Entra ID.
- Can require additional security controls.
- Can block access completely.
- Can enforce MFA.
- Can require a compliant device.

Users
Determines who the policy affects.

Cloud Apps
Determines which applications/resources the policy protects.

Conditions
Determine when the policy should apply.

Grant Controls
Determine what happens when the conditions are met.

Report-only
Allows me to evaluate a policy's effect without actually
enforcing it.

Emergency Access / Break-glass Account
An emergency account should be excluded from important
Conditional Access policies so administrators do not
accidentally lock themselves out of the tenant.

==================================================
IMPORTANT POLICY LOGIC
==================================================

Example:

WHO:
All users

WHAT:
All cloud apps

WHEN:
Every sign-in

THEN:
Require MFA

This means:

All users attempting to access cloud applications must
complete MFA.

Another example:

WHO:
All users

WHAT:
All cloud apps

WHEN:
Sign-in risk = High

THEN:
Block access

==================================================
POLICY 1 — REQUIRE MFA
==================================================

Purpose:

Require users to use MFA when accessing Microsoft 365.

Configuration:

Users:
All users

Exclude:
Emergency access/admin account

Cloud apps:
All cloud apps

Grant:
Require multifactor authentication

State:
On

Expected result:

A test user signing into Microsoft 365 should receive an MFA
requirement.

==================================================
POLICY 2 — BLOCK LEGACY AUTHENTICATION
==================================================

Purpose:

Prevent older authentication methods that do not support
modern authentication and MFA properly.

Configuration:

Users:
All users

Cloud apps:
All cloud apps

Conditions:

Client apps:
- Other clients
- Exchange ActiveSync clients

Grant:
Block access

State:
On

Expected result:

Legacy authentication attempts should be blocked.

==================================================
POLICY 3 — REQUIRE COMPLIANT DEVICE
==================================================

Purpose:

Only allow Windows devices that meet the organisation's
compliance requirements to access Microsoft 365.

Configuration:

Users:
All users

Cloud apps:
Office 365

Conditions:

Device platforms:
Windows

Grant:
Require device to be marked as compliant

State:
Report-only

Expected result:

The policy should evaluate Windows devices without actually
blocking access.

I used Report-only because my lab VM may not currently be
registered/enrolled and compliant in Intune.

==================================================
POLICY 4 — BLOCK HIGH-RISK SIGN-INS
==================================================

Purpose:

Prevent access when Microsoft Entra identifies a sign-in as
high risk.

Configuration:

Users:
All users

Cloud apps:
All cloud apps

Condition:

Sign-in risk:
High

Grant:
Block access

State:
On

Expected result:

A sign-in identified as high risk should be blocked.

==================================================
WHAT CONFUSED ME
==================================================

At first I thought Conditional Access was simply an MFA
feature.

I now understand that MFA is only one possible action.

Conditional Access can also block access, require a compliant
device, or apply different controls depending on the user,
application and sign-in conditions.

==================================================
HOW THIS CONNECTS TO THE JOB
==================================================

Conditional Access is important when troubleshooting Microsoft
365 access problems.

If a user suddenly cannot access Outlook or another Microsoft
365 application, the problem may not be their password or
license.

A Conditional Access policy may be:

- Requiring MFA
- Blocking their device
- Blocking their location
- Blocking legacy authentication
- Requiring device compliance
- Blocking a risky sign-in

As an IT support technician, I need to identify which policy
affected the user's sign-in instead of immediately resetting
their password.

==================================================
EXAM TIPS
==================================================

Remember:

WHO
→ Users/groups/roles

WHAT
→ Cloud apps

WHEN
→ Conditions

THEN
→ Grant/block controls

Important concepts:

- MFA
- Report-only
- Block access
- Require compliant device
- Device platforms
- Sign-in risk
- Client apps
- Legacy authentication
- Emergency access accounts

A policy being created does not mean it should immediately be
turned On. Report-only is useful for testing the effect of a
policy before enforcement.

==================================================
DEFEND QUESTION
==================================================

Question:

"A user travelling abroad can't access their email. What do
you check?"

Answer:

First, I would determine whether the user is actually able to
sign in and what error they receive.

I would then check Microsoft Entra sign-in logs to see whether
the sign-in was successful or blocked.

Because the user is travelling abroad, I would specifically
check Conditional Access policies and location-based
conditions to see whether the new sign-in location triggered
a policy.

I would also check whether MFA was required or failed, whether
the device is compliant, whether the sign-in was considered
risky, and whether a legacy authentication client is being
used.

I would not immediately disable the Conditional Access policy.
I would first identify which policy caused the block and then
determine whether the user's access is legitimate and what the
appropriate fix is.

==================================================
WRONG ANSWERS FROM PRACTICE QUESTIONS
==================================================

Q: [paste question]

Correct answer: [answer]

Why I got it wrong: [honest reason]

What I now know: [correct understanding]