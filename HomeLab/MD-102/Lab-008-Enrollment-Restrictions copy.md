# Lab 008 — Intune Enrollment Scopes and Restrictions

Date: 16 August 2026
Day: 09 of 30-day MD-102 plan

==================================================
GOAL
==================================================

Configure Microsoft Intune automatic enrollment and create
enrollment restrictions that control device platforms,
personally owned devices and the number of devices a user can
enroll.

==================================================
ENVIRONMENT
==================================================

- Microsoft 365 E5 tenant
- Microsoft Intune admin center
- Win10-Lab1
- Microsoft Entra ID
- Test users

==================================================
TASK 1 — CONFIGURE MDM USER SCOPE
==================================================

1. Opened the Intune admin center.

2. Navigated to:

Devices
→ Enroll devices
→ Windows enrollment
→ Automatic enrollment

3. Located:

MDM user scope

4. Set:

MDM user scope:
All

5. Saved the configuration.

Result:

All users are now included in the configured automatic MDM
enrollment scope.

Actual result:

[Record result.]

==================================================
TASK 2 — CREATE DEVICE TYPE RESTRICTION
==================================================

Created an enrollment restriction.

Name:

XYZ-Corporate-Only

Configuration:

Windows MDM:
Allow

Personally owned:
Block

Priority:
1

Assigned to:

All users

Purpose:

Allow Windows device enrollment while preventing personally
owned devices from enrolling under this restriction.

Result:

[Record result.]

==================================================
TASK 3 — CREATE DEVICE LIMIT RESTRICTION
==================================================

Created:

XYZ-Device-Limit

Configuration:

Device limit:
3

Assigned to:

All users

Purpose:

Limit the number of devices a user can enroll.

Result:

[Record result.]

==================================================
TASK 4 — TEST WITH WIN10-LAB1
==================================================

On Win10-Lab1:

1. Opened:

Settings
→ Accounts
→ Access work or school

2. Checked the current organisation connection and enrollment
   state.

3. If necessary, disconnected the existing work/school
   connection.

4. Re-enrolled the device.

5. Checked whether the configured Intune enrollment
   restrictions affected the enrollment.

Expected result:

The Windows platform should be allowed.

A personally owned Windows device should be blocked by the
personally-owned restriction if Intune identifies it as
personally owned.

Actual result:

[Record what happened.]

==================================================
TEST RESULTS
==================================================

| Test | Expected | Actual |
|------|----------|--------|
| MDM User Scope | User included | [result] |
| Windows enrollment | Allowed | [result] |
| Personally owned device | Blocked | [result] |
| Device limit | Maximum 3 | [result] |
| Win10-Lab1 enrollment | Evaluated against restrictions | [result] |

==================================================
IMPORTANT OBSERVATION
==================================================

The enrollment configuration does not simply mean:

"Intune is enabled."

Different settings determine:

WHO can automatically enroll
        ↓
WHAT devices can enroll
        ↓
HOW MANY devices a user can enroll

This allows an organisation to control Intune enrollment more
precisely.

==================================================
WHAT BROKE
==================================================

- MDM scope did not apply.
- Device could not enroll.
- Device was not identified as personally owned.
- Restriction did not appear to apply.
- Existing enrollment prevented testing.
- Device limit was not reached.

==================================================
HOW I FIXED IT
==================================================

Possible checks:

1. Confirmed the user was included in the MDM scope.
2. Checked enrollment restrictions.
3. Checked restriction priority.
4. Checked whether the device was already enrolled.
5. Checked device ownership.
6. Checked the user's existing enrolled devices.
7. Checked Intune enrollment status.

==================================================
LESSONS LEARNED
==================================================

I learned that Intune enrollment has multiple layers of
control.

MDM User Scope determines which users are targeted for
automatic enrollment.

Enrollment restrictions determine what types of devices can
enroll.

Device limits determine how many devices a user can enroll.

These settings work together to control the organisation's
device enrollment strategy.

==================================================
EXAM CONNECTION
==================================================

This lab reinforces:

- Microsoft Intune enrollment
- Automatic enrollment
- MDM User Scope
- Enrollment restrictions
- Device platform restrictions
- Personally owned devices
- Corporate-owned devices
- Device enrollment limits
- Restriction priority
- Windows enrollment

==================================================
REAL JOB CONNECTION
==================================================

If a user says:

"I can't enroll my laptop into Intune."

I would troubleshoot systematically:

1. Check whether the user is in the MDM enrollment scope.
2. Check whether the device platform is allowed.
3. Check whether personally owned devices are blocked.
4. Check enrollment restriction priority.
5. Check whether the user has reached the device limit.
6. Check whether the device is already enrolled.
7. Check Intune enrollment status and error information.

This prevents me from immediately assuming that the problem is
with the user's Windows installation or Intune itself.

==================================================
FINAL RESULT
==================================================

I configured automatic Intune enrollment for users and created
restrictions controlling Windows enrollment, personally owned
devices and the maximum number of devices a user can enroll.

I also tested the configuration using Win10-Lab1 and documented
the enrollment behaviour.