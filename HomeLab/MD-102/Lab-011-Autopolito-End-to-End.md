# Lab 011 — Autopilot End-to-End Test

Date: 19 August 2026
Day: 12 of 30-day MD-102 plan

==================================================
GOAL
==================================================

Test the complete Windows Autopilot deployment process from
Windows reset/OOBE through user sign-in, Intune enrollment and
device configuration.

The objective was to understand what happens to a Windows
device from the moment it is reset until it becomes a managed
corporate device.

==================================================
ENVIRONMENT
==================================================

- Microsoft 365 E5 tenant
- Microsoft Intune
- Microsoft Entra ID
- Windows Autopilot
- Win10-Lab1
- VirtualBox
- M365 test user
- Existing Autopilot deployment profile
- Existing Enrollment Status Page

==================================================
EXPECTED END-TO-END PROCESS
==================================================

The expected process was:

Win10-Lab1
    ↓
Take VM snapshot
    ↓
Reset Windows
    ↓
Windows OOBE
    ↓
Connect to Internet
    ↓
Microsoft identifies Autopilot device
    ↓
Autopilot deployment profile applies
    ↓
User signs in with work account
    ↓
Device joins Entra ID
    ↓
Device enrolls into Intune
    ↓
Enrollment Status Page appears
    ↓
Applications and policies install
    ↓
Windows desktop loads
    ↓
Device becomes managed by Intune

==================================================
TASK 1 — CREATE VM SNAPSHOT
==================================================

Before making major changes to Win10-Lab1, I created a
VirtualBox snapshot.

Purpose:

If the Autopilot test caused problems, I could restore the
machine to its previous working state.

==================================================
TASK 2 — RESET WINDOWS
==================================================

Attempted to navigate to:

Settings
→ Recovery
→ Reset this PC

Selected:

Remove everything
→ Local reinstall
→ Reset

Expected result:

Windows should remove the existing installation/configuration
and start the Out-of-Box Experience.

Actual result:

The reset failed.

Windows displayed an error indicating that the computer could
not be reset and that the reset operation did not complete.

Therefore, the VM never reached the expected clean OOBE stage.

==================================================
TASK 3 — AUTOPILOT OOBE TEST
==================================================

Expected:

After the reset, Windows should start the OOBE process.

The device would connect to the Internet and Autopilot would
identify the device.

The configured Autopilot profile should then determine the
deployment experience.

Actual result:

This stage could not be completed because the Windows reset
failed before OOBE.

==================================================
TASK 4 — USER SIGN-IN
==================================================

Expected:

At OOBE/sign-in, the M365 test user would sign in with their
organisation account.

Expected sequence:

Test user
    ↓
Microsoft Entra authentication
    ↓
Autopilot deployment
    ↓
Entra ID Join
    ↓
Intune enrollment

Actual result:

Not tested because the VM did not successfully reach OOBE.

==================================================
TASK 5 — ENROLLMENT STATUS PAGE
==================================================

Expected:

The Enrollment Status Page should appear during deployment.

It should show the progress of:

- Device configuration
- Application installation
- Policy application

Because the configured ESP was set to block the device until
applications were installed, the user should not receive the
normal desktop until the required deployment stage was
complete.

Actual result:

Not reached because the Windows reset failed.

==================================================
TASK 6 — INTUNE VERIFICATION
==================================================

Expected after successful deployment:

Intune
→ Devices
→ All devices

The device should appear as enrolled.

I would then verify:

- Enrollment status
- Compliance status
- Device ownership
- Assigned configuration profiles
- Applications
- Device configuration
- Entra ID connection

Actual result:

Not completed as part of the end-to-end reset test.

==================================================
TASK 7 — RESTORE SNAPSHOT
==================================================

Because the reset operation failed, the original VM
environment was preserved/restored rather than continuing to
modify the machine.

Purpose:

Return Win10-Lab1 to the known working state used for the
previous labs.

==================================================
WHAT BROKE
==================================================

Windows Reset failed.

Error/message:

"This PC can't be reset. No changes were made."

The failure occurred before Windows could enter the expected
Autopilot OOBE process.

==================================================
HOW I HANDLED IT
==================================================

I did not spend excessive time troubleshooting the Windows
reset because the purpose of this lab was to understand the
Autopilot end-to-end workflow.

I documented the failure and preserved the working VM.

The theoretical deployment process was documented so that I
understand what should happen when the test is performed
successfully on an appropriate device.

==================================================
IMPORTANT OBSERVATION
==================================================

Autopilot does not simply "install Windows."

It works as part of a larger deployment process:

Device identification
        ↓
Autopilot profile
        ↓
Windows OOBE
        ↓
Entra ID
        ↓
Intune enrollment
        ↓
Policies/applications
        ↓
Compliance
        ↓
Managed corporate device

The Autopilot profile determines the deployment experience,
while Intune manages the device after enrollment.


==================================================
LESSONS LEARNED
==================================================

I learned the theoretical end-to-end Autopilot deployment
process even though my VM could not complete the reset.

The important workflow is:

Reset/OOBE
→ Internet
→ Autopilot identification
→ User authentication
→ Entra ID Join
→ Intune enrollment
→ Enrollment Status Page
→ Applications/policies
→ Managed Windows device

I also learned that a failed lab step does not necessarily mean
the Microsoft configuration is wrong. The failure can occur at
the Windows/VM layer before Autopilot is even reached.

==================================================
EXAM CONNECTION
==================================================

This lab reinforces the relationship between:

- Windows OOBE
- Windows Autopilot
- Autopilot deployment profiles
- Microsoft Entra ID
- Intune enrollment
- Enrollment Status Page
- Device compliance
- Application deployment

A useful exam mindset is to identify which stage of the
deployment process a problem occurs in.

==================================================
REAL JOB CONNECTION
==================================================

If a new corporate laptop fails during deployment, I should
identify where the failure occurred.

For example:

Windows cannot reset
→ Investigate Windows/device issue.

Device reaches OOBE but Autopilot does not appear
→ Check Autopilot registration/network/profile assignment.

User cannot sign in
→ Check Entra ID/account/authentication.

Device signs in but does not become managed
→ Check Intune enrollment.

Apps do not install
→ Check Intune application assignment/deployment.

Device is enrolled but not compliant
→ Check compliance policies and device configuration.

This gives me a structured troubleshooting process instead of
assuming every deployment problem is an Intune problem.

==================================================
FINAL RESULT
==================================================

The end-to-end Autopilot test could not be completed because
the Windows Reset this PC operation failed before the VM
reached OOBE.

The failure was documented, the working VM environment was
preserved, and the complete expected Autopilot workflow was
documented conceptually.

The lab is therefore considered a partial hands-on test with
the end-to-end process understood theoretically.