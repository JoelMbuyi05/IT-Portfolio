# Day 09 — Intune Enrollment Scopes

Date: 16 August 2026
Source: Microsoft Learn
- "Set up Microsoft Intune"
- "Configure enrollment restrictions"

==================================================
WHAT I LEARNED TODAY
==================================================

Today I learned how Microsoft Intune controls which users and
devices can automatically enroll into device management.

There are two important areas:

1. MDM User Scope
2. Enrollment Restrictions

MDM User Scope determines which users are automatically
enrolled into Intune when they join or register a device.

The main options are:

All
→ All users are included in automatic MDM enrollment.

Some
→ Only selected users/groups are automatically enrolled.

None
→ Automatic MDM enrollment is not enabled for users.

==================================================
ENROLLMENT RESTRICTIONS
==================================================

Enrollment restrictions control what types of devices users can
enroll into Intune.

There are two important types:

1. Device Type Restrictions
2. Device Limit Restrictions

==================================================
DEVICE TYPE RESTRICTIONS
==================================================

Device type restrictions determine which device platforms can
be enrolled.

Examples:

- Windows
- iOS/iPadOS
- Android
- macOS

They can also control whether personally owned devices are
allowed.

For example:

Windows:
Allow

Personally owned Windows devices:
Block

This can be used when an organisation wants to manage only
company-owned Windows devices and prevent BYOD enrollment.

==================================================
DEVICE LIMIT RESTRICTIONS
==================================================

Device limit restrictions control how many devices a user can
enroll.

Example:

Device limit:
3

This means the user can have up to three enrolled devices under
that restriction.

The default limit can be higher, but an organisation can
reduce the limit depending on its security requirements.

==================================================
KEY CONCEPTS
==================================================

MDM
→ Mobile Device Management.

MDM User Scope
→ Determines which users are automatically enrolled into
  Intune.

Automatic Enrollment
→ Allows devices to automatically become managed by Intune
  when the appropriate enrollment process occurs.

Enrollment Restriction
→ Controls what devices/users are allowed to enroll.

Device Type Restriction
→ Controls platforms and ownership types.

Device Limit
→ Controls the maximum number of devices a user can enroll.

Personally Owned
→ A device owned by the employee rather than the organisation.

==================================================
HOW THIS CONNECTS TO THE JOB
==================================================

If a company wants employees to use only corporate-owned
Windows computers, I can configure Intune enrollment
restrictions to allow Windows devices while blocking
personally owned devices.

If a user says:

"I can't enroll my laptop into Intune."

I should check:

- Is the user included in the MDM User Scope?
- Is the device platform allowed?
- Is the device personally owned?
- Is there an enrollment restriction?
- Has the user reached the device enrollment limit?
- Is another restriction with higher priority being applied?

This gives me a structured approach to troubleshooting
enrollment problems.

==================================================
EXAM TIPS
==================================================

Remember:

MDM User Scope
→ Who gets automatic enrollment.

Device Type Restriction
→ What type of device/platform can enroll.

Device Limit Restriction
→ How many devices a user can enroll.

"All" in MDM User Scope
→ All users are targeted.

"Some"
→ Only selected users/groups.

"None"
→ No users are automatically enrolled.

Also remember that enrollment restrictions can be assigned
and evaluated according to their configured priorities.

==================================================
WHAT CONFUSED ME
==================================================

At first I mixed up MDM User Scope and enrollment restrictions.

I now understand that MDM User Scope answers:

"Who should automatically enroll?"

while enrollment restrictions answer:

"What devices are allowed to enroll?"

==================================================
EXAM CONNECTION
==================================================

MD-102 can test whether I understand the difference between
enrollment configuration and enrollment restrictions.

For example:

A user is unable to enroll a Windows laptop.

I should not immediately assume Intune is broken.

I should check the user's MDM enrollment scope and then check
the device enrollment restrictions and limits.

==================================================
WRONG ANSWERS FROM PRACTICE QUESTIONS
==================================================

Q: [paste question]

Correct answer: [answer]

Why I got it wrong: [honest reason]

What I now know: [correct understanding]