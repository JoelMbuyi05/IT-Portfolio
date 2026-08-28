# Day 18 — Device Compliance Policies

Date: 25 August 2026
Source:
- Microsoft Learn — "Use compliance policies to set rules for devices"

==================================================
WHAT I LEARNED TODAY
==================================================

Today I learned about device compliance policies in Microsoft
Intune.

A compliance policy defines the security requirements that a
device must meet.

Unlike a configuration profile, which actively applies settings,
a compliance policy evaluates the device and determines whether
it is compliant or non-compliant.

The basic idea is:

Device
  ↓
Intune checks requirements
  ↓
Requirements met?
  ↓
Compliant / Non-compliant

==================================================
COMPLIANCE POLICY VS CONFIGURATION PROFILE
==================================================

Compliance policy
→ Checks whether a device meets security requirements.
→ Produces a compliance status.

Configuration profile
→ Pushes settings and configurations to the device.

Example:

Configuration profile:
→ Turn on Windows Firewall.

Compliance policy:
→ Check whether Windows Firewall is turned on.

Simple way to remember:

Configuration:
"Make the device secure."

Compliance:
"Check whether the device is secure."

==================================================
WINDOWS HEALTH ATTESTATION
==================================================

Windows Health Attestation allows Intune to evaluate important
security features of the Windows device.

Important requirements include:

Require BitLocker:
Yes

Require Secure Boot:
Yes

Require Code Integrity:
Yes

These features help protect the device during startup and
protect data stored on the device.

==================================================
DEVICE PROPERTIES
==================================================

Minimum OS version:

10.0.19041

This prevents devices running an older Windows version from
being considered compliant.

Maximum OS version:

Usually left blank unless the organisation specifically needs
to prevent newer/unapproved Windows versions.

==================================================
SYSTEM SECURITY
==================================================

Important compliance requirements include:

Require password:
Yes

Minimum password length:
8

Password complexity:
Required

Maximum inactivity:
15 minutes

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

These settings allow an organisation to establish a minimum
security standard for corporate devices.

==================================================
KEY CONCEPTS
==================================================

Compliance policy
→ Defines security requirements for devices.

Compliant
→ Device meets the required conditions.

Non-compliant
→ One or more required conditions are not met.

BitLocker
→ Encrypts data stored on the Windows device.

Secure Boot
→ Helps prevent unauthorised software from loading during
  the boot process.

Code Integrity
→ Helps ensure trusted code is running on the device.

Firewall
→ Helps control unwanted network traffic.

Antivirus
→ Protects against malicious software.

Encryption
→ Protects data if the device is lost or stolen.

Conditional Access
→ Can use device compliance as a condition before allowing
  access to company resources.

==================================================
WHAT CONFUSED ME
==================================================

I initially thought that a compliance policy automatically
fixed a security problem.

I now understand that compliance policies mainly evaluate the
device.

If a device fails because BitLocker is disabled, I need to
configure BitLocker through an appropriate management method.
The compliance policy then checks whether the requirement has
been satisfied.

==================================================
HOW THIS CONNECTS TO THE JOB
==================================================

If a user reports that they cannot access Microsoft 365, I can
check whether their device is compliant.

For example:

User signs in
      ↓
Conditional Access checks device
      ↓
Intune compliance status
      ↓
Compliant?
   /       \
 Yes       No
 ↓          ↓
Allow      Access blocked
access

This means IT can prevent insecure devices from accessing
company resources.

==================================================
EXAM TIPS
==================================================

Remember:

Compliance policy
→ Evaluates device security.

Configuration profile
→ Applies device settings.

BitLocker
→ Encryption.

Secure Boot
→ Protects the boot process.

Firewall
→ Network protection.

Antivirus / Defender
→ Malware protection.

Minimum OS version
→ Prevents outdated Windows versions.

Conditional Access
→ Can require a compliant device before granting access.

==================================================
WRONG ANSWERS FROM PRACTICE QUESTIONS
==================================================

Q: [paste question]

Correct answer: [answer]

Why I got it wrong: [honest reason]

What I now know: [correct understanding]