# Lab 024 — Compliance Policy and Fixes

Date: 25 August 2026
Day: 18 of 30-day MD-102 plan

==================================================
GOAL
==================================================

Create a Windows compliance policy in Microsoft Intune,
evaluate Win10-Lab1, identify failed compliance requirements,
fix the issues and connect device compliance to Conditional
Access.

==================================================
ENVIRONMENT
==================================================

- Microsoft 365 E5 tenant
- Microsoft Intune
- Microsoft Entra ID
- Win10-Lab1
- Windows 10 and later
- Conditional Access

==================================================
TASK 1 — CREATE COMPLIANCE POLICY
==================================================

Opened:

Intune admin center

Navigated to:

Devices
→ Compliance policies
→ Policies
→ Create

Selected:

Platform:
Windows 10 and later

Created:

Name:
XYZ-Security-Baseline

==================================================
TASK 2 — CONFIGURE WINDOWS HEALTH ATTESTATION
==================================================

Configured:

Require BitLocker:
Yes

Require Secure Boot:
Yes

Require Code Integrity:
Yes

Purpose:

Ensure that important Windows hardware and boot security
features are enabled.

==================================================
TASK 3 — CONFIGURE DEVICE PROPERTIES
==================================================

Configured:

Minimum OS version:
10.0.19041

Maximum OS version:
Blank

Purpose:

Prevent unsupported or outdated Windows versions from being
considered compliant.

==================================================
TASK 4 — CONFIGURE SYSTEM SECURITY
==================================================

Configured:

Require password:
Yes

Minimum password length:
8

Password complexity:
Required

Maximum minutes of inactivity:
15

Require encryption:
Yes

Firewall:
Required

Antivirus:
Required

Antispyware:
Required

Microsoft Defender Antimalware:
Required

==================================================
TASK 5 — ASSIGN POLICY
==================================================

Assigned:

XYZ-Security-Baseline

To:

All Devices

Purpose:

Evaluate the security state of the managed Windows devices.

==================================================
TASK 6 — CHECK WIN10-LAB1 COMPLIANCE
==================================================

Navigated to:

Intune
→ Devices
→ Windows
→ Win10-Lab1
→ Device compliance

Checked the compliance status.

Initial result:

Overall compliance:
[Compliant / Non-compliant]

==================================================
FAILED SETTINGS
==================================================

Documented each setting that failed.

BitLocker:
[Pass / Fail]

Secure Boot:
[Pass / Fail]

Code Integrity:
[Pass / Fail]

Minimum OS version:
[Pass / Fail]

Password:
[Pass / Fail]

Encryption:
[Pass / Fail]

Firewall:
[Pass / Fail]

Antivirus:
[Pass / Fail]

Antispyware:
[Pass / Fail]

Microsoft Defender:
[Pass / Fail]

==================================================
TASK 7 — FIX BITLOCKER
==================================================

If BitLocker was failing:

Opened Windows settings and checked BitLocker/device
encryption.

Enabled encryption where supported.

Verified that Windows recognised the device as encrypted.

Then synchronized the device with Intune.

Result:

BitLocker:
[Pass / Fail]

IMPORTANT:

If BitLocker could not be enabled in the VM because of the
virtual hardware/TPM configuration, I documented the limitation
instead of claiming the requirement was successfully fixed.

==================================================
TASK 8 — FIX WINDOWS FIREWALL
==================================================

Checked Windows Security:

Windows Security
→ Firewall & network protection

Enabled the appropriate firewall protection if it was disabled.

Then synchronized the device with Intune.

Result:

Firewall:
[Pass / Fail]

==================================================
TASK 9 — FIX MICROSOFT DEFENDER
==================================================

Checked:

Windows Security
→ Virus & threat protection

Verified Microsoft Defender Antivirus was enabled.

If disabled, enabled the appropriate protection.

Then synchronized the device.

Result:

Antivirus:
[Pass / Fail]

Antispyware:
[Pass / Fail]

Microsoft Defender Antimalware:
[Pass / Fail]

==================================================
TASK 10 — SYNCHRONIZE DEVICE
==================================================

On Win10-Lab1:

Settings
→ Accounts
→ Access work or school
→ Connected work/school account
→ Info
→ Sync

Waited for Intune to process the updated device status.

Then returned to:

Intune
→ Devices
→ Win10-Lab1
→ Device compliance

Checked the updated compliance result.

Final result:

[Compliant / Non-compliant]

==================================================
TASK 11 — CONNECT COMPLIANCE TO CONDITIONAL ACCESS
==================================================

Returned to Conditional Access.

Located the policy created on Day 8:

Policy 3 — Require compliant device for M365

Previously:

Report-only

Updated to:

On

Policy concept:

Users:
All users

Cloud apps:
Office 365

Conditions:
Windows devices

Grant:
Require device to be marked as compliant

State:
On

IMPORTANT:

Before enabling this in a real environment, an emergency/break-
glass administrator account should be excluded and the policy
should be tested carefully.

==================================================
TASK 12 — TEST CONDITIONAL ACCESS
==================================================

Tested with the appropriate test user/device.

Expected:

Compliant device
→ Access allowed

Non-compliant device
→ Access denied or additional access requirements applied,
  depending on the Conditional Access configuration.

Actual result:

[Record result.]

==================================================
WHAT BROKE
==================================================

- BitLocker could not be enabled.
- Secure Boot was unavailable in the VM.
- Device remained non-compliant after fixing settings.
- Intune compliance status remained stale.
- Defender status was not detected immediately.
- Conditional Access blocked the test account.
- VM hardware did not support a required security feature.

==================================================
HOW I FIXED IT
==================================================

Troubleshooting process:

1. Checked the specific failed compliance setting.
2. Checked the corresponding Windows setting.
3. Corrected the setting where possible.
4. Synchronized Win10-Lab1 with Intune.
5. Waited for the device to report its updated state.
6. Rechecked compliance status.
7. Checked Conditional Access if access was still blocked.

==================================================
LESSONS LEARNED
==================================================

I learned that Intune compliance policies do not simply
configure a device. They evaluate whether the device satisfies
the organisation's security requirements.

I also learned that compliance becomes much more powerful when
combined with Conditional Access.

For example:

Intune
→ Device is evaluated
→ Device is non-compliant
→ Conditional Access checks compliance
→ Access to Microsoft 365 can be blocked

After fixing the security issue:

Device becomes compliant
→ Intune reports compliant
→ Conditional Access allows access

==================================================
EXAM CONNECTION
==================================================

This lab reinforces:

- Intune compliance policies
- Windows Health Attestation
- BitLocker
- Secure Boot
- Code Integrity
- Minimum OS version
- Password requirements
- Encryption
- Windows Firewall
- Microsoft Defender
- Antivirus
- Antispyware
- Compliance status
- Conditional Access
- Require compliant device

==================================================
REAL JOB CONNECTION
==================================================

A company does not want an employee's unmanaged or insecure
laptop accessing company data.

The organisation can create a compliance policy requiring:

- Encryption
- Firewall
- Antivirus
- Supported Windows version
- Strong password
- Secure Boot

Conditional Access can then use the compliance result:

Secure device
→ Compliant
→ Microsoft 365 access allowed

Insecure device
→ Non-compliant
→ Access blocked or restricted

This creates a connection between endpoint security and
identity/access control.

==================================================
FINAL RESULT
==================================================

Created:

XYZ-Security-Baseline

Configured Windows security and compliance requirements,
assigned the policy to devices, checked Win10-Lab1's compliance
status and documented the failed requirements.

Fixed the applicable security settings and synchronized the
device with Intune.

Finally, connected the compliance requirement to the Conditional
Access policy from Day 8.

The main concept I learned is:

Configuration profiles configure the device.
Compliance policies evaluate the device.
Conditional Access uses that result to control access.