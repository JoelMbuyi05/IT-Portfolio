# Lab 010 — Autopilot Deployment Profiles & Enrollment Status Page

Date: 18 August 2026
Day: 11 of 30-day MD-102 plan

==================================================
GOAL
==================================================

Create a Windows Autopilot deployment profile and an Enrollment
Status Page (ESP) to control how a corporate Windows device is
configured during deployment.

==================================================
ENVIRONMENT
==================================================

- Microsoft 365 E5 tenant
- Microsoft Intune admin center
- Microsoft Entra ID
- Windows Autopilot
- Win10-Lab1
- Test device/user group

==================================================
TASK 1 — CREATE AUTOPILOT DEPLOYMENT PROFILE
==================================================

1. Opened:

Intune admin center

2. Navigated to:

Devices
→ Enroll devices
→ Windows enrollment
→ Windows Autopilot deployment profiles

3. Selected:

Create profile

4. Selected:

Windows PC

5. Created:

Name:
XYZ-Standard-Employee

Deployment mode:
User-driven

Join to Entra ID as:
Entra ID joined

==================================================
OUT-OF-BOX EXPERIENCE CONFIGURATION
==================================================

Configured:

Skip privacy settings:
Yes

Skip EULA:
Yes

User account type:
Standard User

Allow White Glove / Pre-Provisioning:
No

Purpose:

This profile is designed for a normal corporate employee who
receives a company Windows laptop and completes the initial
setup using their work account.

==================================================
TASK 2 — CREATE ENROLLMENT STATUS PAGE
==================================================

1. Navigated to:

Devices
→ Enroll devices
→ Enrollment Status Page

2. Selected:

Create

3. Created:

Name:
XYZ-Enrollment-Status

Configured:

Show app installation progress:
Yes

Block device until apps installed:
Yes

Allow reset if install error:
Yes

Purpose:

The Enrollment Status Page provides visibility into the device
deployment process and can prevent the user from using the
device before required applications have finished installing.

==================================================
TASK 3 — ASSIGN THE PROFILES
==================================================

Assigned the Autopilot deployment profile to:

[Device group name]

Assigned the Enrollment Status Page configuration to:

[Device/user group name]

Important:

The group assignment must contain the appropriate devices/users
for the configuration to apply.

==================================================
TASK 4 — REVIEW THE CONFIGURATION
==================================================

Reviewed the Autopilot profile and verified:

Deployment mode:
User-driven

Join type:
Entra ID joined

User account:
Standard user

Privacy settings:
Skipped

EULA:
Skipped

White Glove:
Disabled

Reviewed the Enrollment Status Page:

Application installation progress:
Enabled

Block until applications installed:
Enabled

Reset if installation error:
Enabled

==================================================
TEST
==================================================

Test device:

Win10-Lab1 / [device name]

Test user:

[test user]

Expected behaviour:

The device should use the assigned Autopilot profile during
deployment.

The user should receive the configured OOBE experience.

The Enrollment Status Page should show application/configuration
progress and prevent normal use until required configuration
has completed.

Actual result:

[Record what happened.]

==================================================
WHAT BROKE
==================================================

[Record anything that actually failed.]

Examples:

- Profile did not appear.
- Device was not assigned to the profile.
- ESP did not appear.
- Device was not recognised as an Autopilot device.
- Application installation did not complete.
- Group assignment did not apply.

==================================================
HOW I FIXED IT
==================================================

[Record the actual troubleshooting steps.]

Possible checks:

1. Confirmed the device was registered in Autopilot.
2. Confirmed the device was in the correct group.
3. Checked Autopilot profile assignment.
4. Checked ESP configuration.
5. Checked Intune device enrollment.
6. Checked Entra ID device status.
7. Checked application assignment.
8. Checked Intune deployment status.

==================================================
LESSONS LEARNED
==================================================

I learned that an Autopilot deployment profile controls how a
Windows device behaves during its initial setup.

I also learned that different deployment modes exist for
different scenarios.

User-Driven is suitable for normal employees.

Self-Deploying is useful for devices such as kiosks and shared
devices.

Pre-Provisioning allows IT to prepare devices before giving
them to users.

The Enrollment Status Page provides additional control over
the deployment process by showing installation progress and
potentially preventing access until required configuration is
complete.

==================================================
EXAM CONNECTION
==================================================

This lab reinforces:

- Windows Autopilot
- Deployment profiles
- User-Driven deployment
- Self-Deploying deployment
- Pre-Provisioning
- Existing Devices
- Entra ID Join
- Standard User
- OOBE
- Enrollment Status Page
- Application deployment
- Intune device enrollment
- Autopilot group assignment

==================================================
REAL JOB CONNECTION
==================================================

Imagine the company hires 50 new employees.

Instead of IT manually configuring 50 laptops:

Traditional approach:

50 laptops
→ manually configure each device
→ install applications
→ configure policies
→ create accounts
→ deliver devices

Autopilot approach:

Register devices
→ assign Autopilot profile
→ assign Intune applications/policies
→ ship devices
→ users connect to Internet
→ Autopilot performs deployment

This allows IT to standardise deployment while reducing
manual configuration work.

==================================================
FINAL RESULT
==================================================

I created a User-Driven Windows Autopilot deployment profile
for standard corporate employees.

I also created an Enrollment Status Page that displays
application installation progress and can prevent access until
required applications are installed.

I now understand how Autopilot profiles determine the
deployment experience and how Intune controls the device after
enrollment.