# TJ-009 — Autopilot End-to-End Test Failure

Date: 19 August 2026
Related Lab: Lab 019 — Autopilot End-to-End Test
System: Win10-Lab1
Environment: Windows 11 VM / VirtualBox

==================================================
PROBLEM
==================================================

I attempted to reset Win10-Lab1 using:

Settings
→ Recovery
→ Reset this PC
→ Remove everything
→ Local reinstall

The reset failed.

Windows displayed an error indicating that the PC could not be
reset and that no changes were made.

==================================================
EXPECTED RESULT
==================================================

The VM should have:

1. Reset Windows.
2. Started the Windows OOBE.
3. Connected to the Internet.
4. Allowed Autopilot to identify the device.
5. Applied the Autopilot deployment profile.
6. Allowed the M365 test user to sign in.
7. Enrolled the device into Intune.
8. Displayed the Enrollment Status Page.

==================================================
ACTUAL RESULT
==================================================

The Windows reset failed before the VM reached OOBE.

Therefore, the Autopilot deployment process could not be
tested end-to-end.

==================================================
INITIAL ANALYSIS
==================================================

The failure occurred during the Windows reset stage.

This means the failure happened before:

- Autopilot
- Entra ID authentication
- Intune enrollment
- Enrollment Status Page

could be properly tested.

Therefore, I should not immediately assume that the Autopilot
configuration is responsible for the failure.

==================================================
TROUBLESHOOTING APPROACH
==================================================

I would investigate:

1. Windows recovery environment
2. Windows system files
3. VM disk/storage configuration
4. VirtualBox configuration
5. Windows installation health
6. Alternative reset/reinstallation methods

However, I decided not to spend excessive time on this issue
because the objective of the 30-day MD-102 lab was to understand
the Autopilot workflow rather than repair the VM's Windows
recovery environment.

==================================================
ACTION TAKEN
==================================================

Documented the failure.

Preserved/restored the working VM environment.

Documented the expected Autopilot end-to-end workflow
theoretically.

Moved on to the next MD-102 topic.

==================================================
LESSON LEARNED
==================================================

When troubleshooting a complex process, identify exactly which
stage failed.

In this case:

Windows Reset
    ↓
FAILED HERE
    ↓
OOBE
    ↓
Autopilot
    ↓
Entra ID
    ↓
Intune

Because the failure happened before Autopilot, I should not
blame Autopilot without evidence.

==================================================
FINAL STATUS
==================================================

Status: PARTIAL / BLOCKED BY VM

Autopilot theory: Completed

Autopilot configuration: Completed in previous labs

End-to-end hands-on test: Not completed

Reason:
Windows Reset failed before OOBE.