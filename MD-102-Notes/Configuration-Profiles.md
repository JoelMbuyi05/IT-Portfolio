# Day 15 — Intune Configuration Profiles

Date: 22 August 2026
Source:
- Microsoft Learn — "Configure device profiles in Microsoft Intune"

==================================================
WHAT I LEARNED TODAY
==================================================

Today I learned about configuration profiles in Microsoft
Intune and how they are used to actively configure settings on
managed devices.

A configuration profile pushes settings from Intune to devices.

This is different from a compliance policy.

==================================================
CONFIGURATION PROFILE VS COMPLIANCE POLICY
==================================================

Configuration profile
→ Tells the device what settings to use.
→ Actively configures the device.

Compliance policy
→ Defines the requirements a device must meet.
→ Produces a compliance status such as compliant or
  non-compliant.

Simple way to remember:

Configuration profile
→ "Configure the device this way."

Compliance policy
→ "Check whether the device meets these requirements."

Example:

Configuration profile:
→ Require a screen lock after 5 minutes.

Compliance policy:
→ Device must have a password and meet the organisation's
  security requirements.

==================================================
CONFIGURATION PROFILE TYPES
==================================================

Settings Catalog
→ Provides individual settings that can be searched and
  configured.
→ Flexible and commonly used for modern Intune configuration.

Templates
→ Pre-built profiles designed for common configuration tasks.

Administrative Templates
→ Provide settings similar to traditional Group Policy
  settings.
→ Useful for administrators familiar with on-premises GPOs.

Custom
→ Uses OMA-URI settings.
→ Useful for advanced settings that are not available through
  the normal Intune interface.

==================================================
PROFILE 1 — SECURITY SETTINGS
==================================================

I created a Windows 10 and later Settings Catalog profile.

Security settings configured included:

USB
→ Allow USB connection: Block

Control Panel
→ Allow Control Panel: Block

Lock screen
→ Configure lock screen message

Message:

"XYZ Technology Solutions — Property tag: [asset number]"

Purpose:

These settings demonstrate how an organisation can centrally
control device behaviour and apply security-related
configuration.

==================================================
PROFILE 2 — PASSWORD SETTINGS
==================================================

I created a password configuration profile.

Settings:

Require password:
Yes

Minimum password length:
10 characters

Password complexity:
Required

Maximum inactivity before lock:
5 minutes

Purpose:

This profile improves device security by requiring stronger
passwords and automatically locking inactive devices.

==================================================
PROFILE 3 — MICROSOFT EDGE SETTINGS
==================================================

I created a Microsoft Edge configuration profile.

Settings:

Homepage URL:
https://intune.microsoft.com/#home

InPrivate browsing:
Disabled

Purpose:

An organisation can use Intune to standardise browser
configuration across managed company devices.

==================================================
KEY CONCEPTS
==================================================

Configuration Profile
→ Pushes settings to managed devices.

Settings Catalog
→ Flexible collection of individual settings.

Administrative Templates
→ Intune equivalent of many familiar Group Policy settings.

OMA-URI
→ Advanced/custom configuration method.

Assignment
→ Determines which users or devices receive the profile.

Device Sync
→ Allows the device to communicate with Intune and receive
  updated configuration.

==================================================
WHAT CONFUSED ME
==================================================

At first I mixed up configuration profiles and compliance
policies.

I now understand that a configuration profile changes/configures
the device, while a compliance policy evaluates whether the
device meets defined requirements.

==================================================
HOW THIS CONNECTS TO THE JOB
==================================================

Instead of manually configuring every computer, an IT
administrator can create a configuration profile once and
assign it to many devices.

For example:

100 company laptops
        ↓
One Intune configuration profile
        ↓
Assigned to device group
        ↓
Settings pushed automatically

This makes device configuration consistent and easier to
manage.

==================================================
EXAM TIPS
==================================================

Remember:

Configuration profile
→ Applies settings.

Compliance policy
→ Evaluates compliance.

Settings Catalog
→ Individual settings; flexible.

Administrative Templates
→ Group Policy-like settings.

Custom OMA-URI
→ Advanced/custom settings.

Also remember that a profile only affects the users/devices
included in its assignment.

==================================================
WRONG ANSWERS FROM PRACTICE QUESTIONS
==================================================

Q: [paste question]

Correct answer: [answer]

Why I got it wrong: [honest reason]

What I now know: [correct understanding]