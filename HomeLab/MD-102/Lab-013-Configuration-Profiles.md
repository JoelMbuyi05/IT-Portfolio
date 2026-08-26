# Lab 013 — Intune Configuration Profiles

Date: 22 August 2026
Day: 15 of 30-day MD-102 plan

==================================================
GOAL
==================================================

Create and test Windows configuration profiles in Microsoft
Intune.

The objective is to understand how Intune centrally pushes
configuration settings to managed Windows devices.

==================================================
ENVIRONMENT
==================================================

- Microsoft 365 E5 tenant
- Microsoft Intune
- Microsoft Entra ID
- Win10-Lab1
- Windows 10 and later configuration profiles

==================================================
TASK 1 — SECURITY SETTINGS PROFILE
==================================================

1. Opened:

Intune admin center

2. Navigated to:

Devices
→ Configuration profiles
→ Create profile

3. Selected:

Platform:
Windows 10 and later

Profile type:
Settings catalog

4. Created a profile for security settings.

Profile name:

XYZ-Security-Settings

==================================================
USB CONFIGURATION
==================================================

Searched Settings Catalog for:

USB

Configured:

Allow USB Connection:
Block

Purpose:

Demonstrate how Intune can control peripheral/device access.

==================================================
CONTROL PANEL CONFIGURATION
==================================================

Searched:

Control Panel

Configured:

Allow Control Panel:
Block

Purpose:

Restrict access to Control Panel settings.

==================================================
LOCK SCREEN CONFIGURATION
==================================================

Searched:

Lock screen

Configured a lock screen message:

"XYZ Technology Solutions — Property tag: [asset number]"

Purpose:

Demonstrate how company information can be displayed on
managed devices.

==================================================
TASK 2 — PASSWORD SETTINGS PROFILE
==================================================

Created another Windows 10 and later Settings Catalog profile.

Profile name:

XYZ-Password-Policy

Configured:

Require password:
Yes

Minimum password length:
10

Password complexity:
Required

Maximum inactivity before lock:
5 minutes

Purpose:

Increase the security of company Windows devices.

==================================================
TASK 3 — MICROSOFT EDGE PROFILE
==================================================

Created another configuration profile.

Profile name:

XYZ-Edge-Configuration

Searched Settings Catalog for:

Microsoft Edge

Configured:

Homepage URL:
https://intune.microsoft.com/#home

Disable InPrivate browsing:
Yes

Purpose:

Standardise Microsoft Edge configuration on company devices.

==================================================
TASK 4 — ASSIGN PROFILES
==================================================

Assigned the configuration profiles to:

All Devices

Profiles:

1. XYZ-Security-Settings
2. XYZ-Password-Policy
3. XYZ-Edge-Configuration

==================================================
TASK 5 — SYNC WIN10-LAB1
==================================================

On Win10-Lab1, I triggered an Intune synchronization.

The device can also be given time to check in automatically.

Expected process:

Intune
    ↓
Configuration profile assigned
    ↓
Device checks in
    ↓
Configuration downloaded
    ↓
Settings applied
    ↓
Device reports status to Intune

Command used if required:

gpupdate /force

Important:

gpupdate /force is primarily for traditional Group Policy and
does not directly force an Intune MDM sync.

For Intune, the better method is to use:

Settings
→ Accounts
→ Access work or school
→ Connected work/school account
→ Info
→ Sync

Or trigger Sync from the Intune admin center.

==================================================
TASK 6 — VERIFY PROFILE STATUS
==================================================

In Intune:

Devices
→ Configuration profiles
→ Selected profile
→ Device/User status

Checked whether Win10-Lab1 received the profiles.

Expected:

Succeeded:
Device received and applied the profile.

Pending:
Device has not completed processing the profile.

Error:
The device encountered a problem applying the profile.

Conflict:
Another configuration may be attempting to configure the
same setting differently.

==================================================
WHAT BROKE
==================================================

- Profile remained Pending.
- Setting did not apply.
- Device showed an error.
- Setting conflicted with an existing policy.
- Edge setting did not apply.
- Device did not immediately check in.

==================================================
HOW I FIXED IT
==================================================

Possible troubleshooting process:

1. Confirmed Win10-Lab1 was enrolled in Intune.
2. Confirmed the device was included in the assignment.
3. Checked profile assignment status.
4. Triggered an Intune device sync.
5. Checked for conflicting policies.
6. Checked Intune error information.
7. Checked the local Windows setting.
8. Rechecked the profile after synchronization.

==================================================
LESSONS LEARNED
==================================================

I learned that Intune configuration profiles are used to
actively push settings to managed devices.

I also learned the important difference between configuration
profiles and compliance policies.

Configuration profile:
→ Configures the device.

Compliance policy:
→ Evaluates whether the device meets requirements.

I also learned that Settings Catalog provides a flexible way
to find and configure individual Windows settings.

==================================================
EXAM CONNECTION
==================================================

This lab reinforces:

- Intune configuration profiles
- Settings Catalog
- Administrative Templates
- Custom OMA-URI
- Windows configuration
- Profile assignments
- Device synchronization
- Configuration status
- Policy conflicts
- Compliance vs configuration

==================================================
REAL JOB CONNECTION
==================================================

In a company with hundreds of Windows computers, manually
configuring every machine would be inefficient and could cause
inconsistent settings.

Instead, an administrator can create an Intune configuration
profile and assign it to a device group.

For example:

XYZ-Security-Settings
        ↓
All corporate Windows devices
        ↓
USB restrictions
Control Panel restrictions
Lock screen configuration

If the organisation changes the requirement later, IT can
modify the central profile rather than manually changing every
computer.

==================================================
FINAL RESULT
==================================================

Created three Intune configuration profiles:

1. XYZ-Security-Settings
2. XYZ-Password-Policy
3. XYZ-Edge-Configuration

Assigned the profiles to the appropriate devices and verified
their deployment status.

I now understand how Intune configuration profiles centrally
apply settings to managed Windows devices and how they differ
from compliance policies.