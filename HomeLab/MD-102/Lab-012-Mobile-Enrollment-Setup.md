# Lab 012 — Mobile Enrollment Setup

Date: 20 August 2026
Duration: [actual time spent]
Day: 13 of 30-day MD-102 plan

==================================================
GOAL
==================================================

Explore how Microsoft Intune handles iOS/iPadOS and Android
enrollment and configure basic mobile device restrictions and
Wi-Fi configuration.

==================================================
ENVIRONMENT
==================================================

- Microsoft 365 E5 tenant
- Microsoft Intune admin center
- Microsoft Entra ID
- Apple enrollment configuration
- Android Enterprise
- Managed Google Play

==================================================
TASK 1 — EXPLORE APPLE ENROLLMENT
==================================================

1. Opened:

Intune admin center

2. Navigated to:

Devices
→ Enroll devices
→ Apple enrollment

3. Explored:

Apple MDM Push certificate

4. Reviewed what is required to configure Apple device
   management.

Important requirement:

Apple device management requires an Apple MDM Push certificate.

For a complete enterprise deployment, Apple Business Manager
can also be integrated with Intune for automated device
enrollment.

Result:

I did not complete the Apple configuration because the lab
does not have the required Apple enterprise setup.

==================================================
TASK 2 — EXPLORE ANDROID ENROLLMENT
==================================================

1. Navigated to:

Devices
→ Enroll devices
→ Android enrollment

2. Located:

Managed Google Play

3. Explored the process for connecting Intune to Managed
   Google Play.

Purpose:

The connection allows Intune to manage Android Enterprise
applications and enrollment.

Result:

[Record whether the connection was completed.]

If completed:

Managed Google Play:
Connected

If not completed:

The setup was explored but not completed.

==================================================
TASK 3 — CREATE MOBILE ENROLLMENT RESTRICTION
==================================================

Created an enrollment restriction for mobile devices.

Configuration:

Platforms:

Android
iOS/iPadOS

Personally owned:
Block

Corporate owned:
Allow

Purpose:

Prevent employees from enrolling personal mobile devices while
allowing corporate-owned mobile devices.

This would be useful for an organisation that wants to prevent
BYOD while still supporting company-issued phones.

Result:

[Record result.]

==================================================
TASK 4 — CREATE CORPORATE WI-FI PROFILE
==================================================

Navigated to:

Devices
→ Configuration profiles
→ Create

Selected:

Platform:
iOS/iPadOS

Profile type:
Wi-Fi

Configured:

Wi-Fi type:
Enterprise

Network name:
XYZ-Corporate

SSID:
XYZ-Corporate

Security type:
WPA2-Enterprise

Purpose:

Automatically provide corporate iOS/iPadOS devices with the
organisation's Wi-Fi configuration.

==================================================
TASK 5 — ASSIGN WI-FI PROFILE
==================================================

Assigned the profile to:

All Devices
→ iOS/iPadOS devices

Result:

[Record result.]

==================================================
WHAT BROKE
==================================================

[Record anything that actually failed.]

Possible limitations:

- Apple MDM Push certificate could not be configured.
- Apple Business Manager was unavailable.
- No physical iOS device was available for testing.
- Managed Google Play connection required additional setup.
- Wi-Fi profile could not be tested without a compatible device
  and network.

==================================================
HOW I HANDLED IT
==================================================

I documented the configuration process and requirements even
where the physical platform/account was unavailable.

The objective was to understand how Intune handles mobile
enrollment rather than pretending that an unsupported device
was successfully enrolled.

==================================================
SCREENSHOTS
==================================================

Save screenshots in:

HomeLab/screenshots/Day-13/

Recommended screenshots:

1. Apple enrollment page
2. Apple MDM Push certificate configuration
3. Android enrollment page
4. Managed Google Play setup
5. Enrollment restriction
6. Personally owned = Block
7. Corporate owned = Allow
8. iOS/iPadOS Wi-Fi profile
9. XYZ-Corporate SSID configuration
10. Profile assignment

==================================================
LESSONS LEARNED
==================================================

I learned that Intune mobile management is different depending
on the platform and ownership model.

For Apple devices, organisations commonly use Apple Business
Manager and Automated Device Enrollment for corporate devices.

For Android, Android Enterprise provides different management
models such as Fully Managed, Work Profile and Dedicated.

I also learned that Intune can enforce enrollment restrictions
and push configuration such as corporate Wi-Fi settings.

==================================================
EXAM CONNECTION
==================================================

This lab reinforces:

- Intune mobile device management
- Apple Business Manager
- Automated Device Enrollment
- Apple MDM Push certificate
- User Enrollment
- Device Enrollment
- Android Enterprise
- Fully Managed
- Work Profile
- Dedicated devices
- Managed Google Play
- Enrollment restrictions
- Corporate vs personal devices
- Configuration profiles
- Wi-Fi profiles

==================================================
REAL JOB CONNECTION
==================================================

Imagine a company has:

100 corporate Android phones
50 corporate iPhones
and employees who want to use personal phones.

IT can use different enrollment methods depending on the
device:

Corporate Android
→ Android Enterprise Fully Managed

Personal Android
→ Work Profile

Corporate iPhone
→ Apple Business Manager + ADE

Personal iPhone
→ User Enrollment

IT can then apply policies and configuration while maintaining
the appropriate level of control over corporate and personal
devices.

==================================================
FINAL RESULT
==================================================

I explored Apple and Android enrollment options in Intune,
reviewed the Apple MDM Push certificate requirements, explored
Managed Google Play, created mobile enrollment restrictions and
configured an iOS/iPadOS corporate Wi-Fi profile.

Where physical Apple/Android devices or required enterprise
accounts were unavailable, I documented the configuration
conceptually rather than claiming a successful enrollment.