# Lab 007 — Conditional Access

Date: 15 August 2026
Day: 08 of 30-day MD-102 plan

==================================================
GOAL
==================================================

Create and test Conditional Access policies in Microsoft Entra
ID to understand how access can be controlled based on users,
applications, conditions and security requirements.

==================================================
ENVIRONMENT
==================================================

- Microsoft 365 E5 tenant
- Microsoft Entra admin center
- Microsoft 365 test users
- Windows lab VM
- Microsoft Intune
- Private browser window

IMPORTANT:

Before creating policies that apply to all users, make sure
there is an emergency/break-glass account excluded from the
policy.

==================================================
TASK 1 — REQUIRE MFA FOR ALL USERS
==================================================

Created a Conditional Access policy.

Policy name:

CA01 — Require MFA for All Users

Configuration:

Users:
All users

Excluded:
Emergency access/admin account

Cloud apps:
All cloud apps

Grant:
Require multifactor authentication

State:
On

Test:

1. Opened a private browser window.
2. Signed in as a test user.
3. Attempted to access Microsoft 365.

Expected result:

The user was required to complete MFA.

Actual result:

[Record what happened.]

Observation:

The policy successfully enforced MFA for the targeted user.

==================================================
TASK 2 — BLOCK LEGACY AUTHENTICATION
==================================================

Created:

CA02 — Block Legacy Authentication

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

Test:

Attempted to use an authentication method/client covered by
the policy.

Expected result:

Legacy authentication should be blocked.

Actual result:

[Record result.]

Observation:

The policy prevents authentication methods that do not support
modern authentication properly.

==================================================
TASK 3 — REQUIRE COMPLIANT WINDOWS DEVICE
==================================================

Created:

CA03 — Require Compliant Windows Device

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

Test:

Signed into Microsoft 365 using the Windows lab VM.

Checked the Conditional Access policy evaluation/sign-in
results.

Expected result:

The policy should be evaluated but should not actually block
the user because it is in Report-only mode.

Actual result:

[Record result.]

Observation:

Report-only is useful when testing a policy before enforcement.

It allows me to see the potential effect without immediately
blocking users.

==================================================
TASK 4 — BLOCK HIGH-RISK SIGN-INS
==================================================

Created:

CA04 — Block High Risk Sign-ins

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

Test:

[Record how the policy was evaluated/tested.]

Expected result:

A sign-in classified as high risk should be blocked.

Actual result:

[Record result.]

Important:

Do not attempt to artificially create dangerous sign-in
conditions just to force the policy to trigger.

The purpose of this lab is to understand the configuration and
how the policy would evaluate a high-risk sign-in.

==================================================
POLICY SUMMARY
==================================================

| Policy | Who | What | When | Then | State |
|--------|-----|------|------|------|-------|
| CA01 — Require MFA | All users | All cloud apps | Sign-in | Require MFA | On |
| CA02 — Block Legacy Auth | All users | All cloud apps | Legacy client | Block | On |
| CA03 — Require Compliant Device | All users | Office 365 | Windows | Require compliant device | Report-only |
| CA04 — Block High Risk | All users | All cloud apps | High sign-in risk | Block | On |

==================================================
WHAT BROKE
==================================================

Examples:

- Policy did not apply.
- Test user was excluded.
- MFA was not triggered.
- Sign-in was blocked unexpectedly.
- Device did not appear compliant.
- Conditional Access policy showed Report-only instead of
  enforcing.

==================================================
HOW I FIXED IT
==================================================

Possible troubleshooting steps:

1. Checked the user was included in the policy.
2. Checked the application targeted by the policy.
3. Checked policy conditions.
4. Checked exclusions.
5. Checked the policy state.
6. Checked Microsoft Entra sign-in logs.
7. Checked Conditional Access evaluation results.

==================================================
LESSONS LEARNED
==================================================

I learned that Conditional Access is a decision-making system
for controlling access.

The basic structure is:

WHO
+
WHAT
+
WHEN
↓
THEN

For example:

All users
+
All cloud apps
+
Sign-in
↓
Require MFA

Or:

All users
+
All cloud apps
+
High sign-in risk
↓
Block access

I also learned that Report-only mode is useful for safely
testing policies before enforcing them.

==================================================
EXAM CONNECTION
==================================================

This lab reinforces:

- Conditional Access
- MFA
- Cloud apps
- Users and groups
- Conditions
- Device platforms
- Client apps
- Sign-in risk
- Grant controls
- Block access
- Require compliant device
- Report-only mode
- Emergency access accounts
- Conditional Access troubleshooting

==================================================
REAL JOB CONNECTION
==================================================

If a user reports:

"I can't access Outlook while travelling."

I should not immediately reset their password.

I would investigate:

1. Microsoft Entra sign-in logs
2. Conditional Access policies
3. Sign-in location
4. Sign-in risk
5. MFA requirements
6. Device compliance
7. Client application
8. Whether the user is being blocked by a specific policy

I would identify the exact policy causing the problem before
making any changes.

==================================================
FINAL RESULT
==================================================

I created four Conditional Access policies and tested their
configuration and behaviour.

The lab demonstrated how Microsoft Entra can use user identity,
application, device and sign-in conditions to determine whether
a user should be allowed access, required to complete MFA, or
blocked.