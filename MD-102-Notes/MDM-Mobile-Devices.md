# Day 13 — Mobile Device Management

Date: 20 August 2026
Source:
- Microsoft Learn — "Enroll iOS and Android devices in Intune"

==================================================
WHAT I LEARNED TODAY
==================================================

Today I learned how Microsoft Intune manages mobile devices,
particularly iOS/iPadOS and Android devices.

Unlike Windows devices, mobile devices have different
enrollment methods depending on whether the device is
corporate-owned or personally owned.

The main idea is:

Corporate device
→ Organisation has greater control
→ More complete device management

Personal/BYOD device
→ User owns the device
→ Management should protect company data without taking
  unnecessary control over personal information

==================================================
IOS / IPADOS ENROLLMENT
==================================================

Apple Business Manager (ABM)
→ Apple's platform for organisations to manage and purchase
  Apple devices at scale.

Automated Device Enrollment (ADE)
→ Automatically enrolls corporate Apple devices into
  management during device setup.

User Enrollment
→ Designed mainly for BYOD/personal Apple devices.
→ Provides management of work data while maintaining separation
  from personal information.

Device Enrollment
→ Used for corporate-owned Apple devices that require more
  management than User Enrollment.

==================================================
ANDROID ENROLLMENT
==================================================

Android Enterprise
→ Microsoft's modern/recommended approach for managing Android
  devices through Intune.

There are several Android Enterprise scenarios.

Fully Managed
→ Corporate-owned device
→ Organisation has extensive control
→ Suitable for company phones assigned to individual users

Work Profile
→ Usually used for BYOD
→ Separates work applications/data from personal applications
  and data

Dedicated
→ Used for devices with a specific purpose
→ Examples:
  - Kiosks
  - Shared devices
  - Point-of-sale devices

Device Administrator
→ Older Android management method
→ Considered legacy and is being phased out in favour of
  Android Enterprise

==================================================
CORPORATE VS PERSONAL DEVICES
==================================================

Corporate-owned:

- Enrolled through organisational provisioning
- Can be registered before deployment
- May have serial/device information associated with the
  organisation
- Organisation can apply stronger management policies

Personal/BYOD:

- User owns the device
- Usually enrolled by the user
- Organisation should focus on protecting corporate data
- Personal data should remain separated/protected

==================================================
KEY CONCEPTS
==================================================

MDM
→ Mobile Device Management.

BYOD
→ Bring Your Own Device.

Apple Business Manager
→ Apple's enterprise device management/provisioning platform.

ADE
→ Automated Device Enrollment for Apple devices.

Android Enterprise
→ Modern Android management framework.

Work Profile
→ Separates work data from personal data on an Android
  personal device.

Fully Managed
→ Full organisational management of a corporate Android
  device.

Dedicated
→ Android device configured for a specific purpose such as
  a kiosk.

Managed Google Play
→ Google Play environment used by organisations to manage
  Android applications through Intune.

==================================================
WHAT CONFUSED ME
==================================================

At first I thought Intune managed all mobile devices in the
same way.

I now understand that the enrollment method depends heavily on
the platform and ownership of the device.

A corporate Android phone can use Fully Managed enrollment,
while a personal Android phone can use a Work Profile to keep
company information separate from personal information.

==================================================
HOW THIS CONNECTS TO THE JOB
==================================================

If a company gives employees Android or iPhones, IT needs to
decide how those devices should be managed.

For example:

Company Android phone
→ Android Enterprise Fully Managed

Employee's personal Android phone
→ Work Profile

Company kiosk
→ Dedicated Android enrollment

Company iPhone fleet
→ Apple Business Manager + Automated Device Enrollment

This allows IT to balance security, management and user
privacy.

==================================================
EXAM TIPS
==================================================

Remember:

Apple:

ABM
→ Organisation's Apple device management/provisioning platform.

ADE
→ Automated corporate Apple enrollment.

User Enrollment
→ Personal/BYOD Apple devices.

Android:

Fully Managed
→ Corporate device.

Work Profile
→ BYOD/personal device.

Dedicated
→ Kiosk/shared/single-purpose device.

Device Administrator
→ Legacy Android management.

==================================================
WRONG ANSWERS FROM PRACTICE QUESTIONS
==================================================

Q: [paste question]

Correct answer: [answer]

Why I got it wrong: [honest reason]

What I now know: [correct understanding]