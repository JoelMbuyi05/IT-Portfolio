# Day 06 — Entra ID Device Registration

Date: 13 August 2026
Source: Microsoft Learn — "Manage device registration in Microsoft Entra"

==================================================
WHAT I LEARNED TODAY
==================================================

Today I learned how devices can be registered or joined to
Microsoft Entra ID and the difference between the three main
device identity states:

1. Entra ID Registered
2. Entra ID Joined
3. Hybrid Entra ID Joined

The important difference is the type of device and how much
control the organisation needs over it.

Entra ID Registered is mainly for personal/BYOD devices.
The user adds their work account to their personal computer
or phone. The organisation can get some visibility and apply
limited management, while the device remains personally owned.

Entra ID Joined is mainly for corporate devices. The device
is joined directly to Microsoft Entra ID and can be fully
managed through Microsoft Intune. It is suitable for
cloud-first organisations that do not need traditional
on-premises Active Directory.

Hybrid Entra ID Joined is used when an organisation still has
on-premises Active Directory but also wants the device to
appear in Microsoft Entra ID. The device is joined to the
traditional AD domain and registered with Entra ID.

==================================================
KEY CONCEPTS
==================================================

Entra ID Registered
- Usually personal/BYOD devices
- Device remains personally owned
- User adds a work account
- Less management than a corporate device
- Useful when employees use their own computers or phones

Entra ID Joined
- Usually corporate-owned devices
- Cloud-first device identity
- Does not require traditional on-premises AD
- Can be managed through Intune
- Provides stronger organisational control

Hybrid Entra ID Joined
- Corporate device
- Joined to on-premises Active Directory
- Also connected to Microsoft Entra ID
- Used by organisations with existing on-premises AD
- Allows organisations to use both traditional AD and
  Microsoft cloud services

==================================================
IMPORTANT COMPARISON
==================================================

| Feature | Entra Registered | Entra Joined | Hybrid Joined |
|---------|------------------|--------------|---------------|
| Typical ownership | Personal | Corporate | Corporate |
| On-prem AD required | No | No | Yes |
| Cloud identity | Yes | Yes | Yes |
| Full organisational management | Limited | Strong | Strong |
| Common use | BYOD | Cloud-first | Hybrid organisations |

==================================================
WHAT I OBSERVED
==================================================

I registered my Win10-Lab1 VM using:

Settings
→ Accounts
→ Access work or school
→ Connect

I signed in using my Microsoft 365 tenant account.

I then checked:

entra.microsoft.com
→ Devices
→ All devices

I located my VM and checked its device information and join
type.

The information available included details such as:

- Device name
- Operating system
- OS version
- Join type
- Device ID
- Compliance information where available
- Last activity/last seen information

==================================================
ENTRA ID VS INTUNE
==================================================

Entra ID focuses primarily on the device's identity and its
relationship with the organisation.

Intune focuses more heavily on device management.

Entra ID can tell me things such as:

- What device it is
- Who it is associated with
- Its join/registration state
- Operating system information
- Device identity information

Intune provides additional management information such as:

- Device management status
- Compliance state
- Configuration policies
- Device ownership
- Management information
- Security/configuration status
- Applications and policies assigned to the device

Therefore:

Entra ID = identity and access

Intune = device management

==================================================
WHAT CONFUSED ME
==================================================

At first I thought Entra ID Registered and Entra ID Joined
were basically the same thing because both connect a device
to Microsoft Entra ID.

I now understand that the important difference is the level
of organisational ownership and control.

Registered is more appropriate for personal/BYOD devices,
while Joined is normally used for organisation-owned devices
that need stronger management.

==================================================
HOW THIS CONNECTS TO THE JOB
==================================================

When supporting users, I need to understand what type of device
the user has and how that device is connected to the
organisation.

For example, if an employee uses their personal laptop, I
would not automatically treat it like a company-owned device.

A personal device may be Entra ID Registered, while a company
laptop could be Entra ID Joined and managed through Intune.

This affects what policies, applications, security controls
and troubleshooting steps are available to me.

==================================================
EXAM TIPS
==================================================

- Registered = usually personal/BYOD.
- Joined = usually corporate/cloud-first.
- Hybrid Joined = corporate + on-premises AD + Entra ID.
- Entra Registered does not mean the device is fully joined
  to the organisation.
- Entra Joined does not require traditional on-premises AD.
- Hybrid Joined is for organisations that still use
  on-premises Active Directory.
- Intune is primarily the device-management platform.
- Entra ID provides the device identity and access layer.

==================================================
DEFEND QUESTION
==================================================

Question:

"What's the difference between Entra ID Registered and
Entra ID Joined? When would you use each?"

Answer:

Entra ID Registered is mainly for personal or BYOD devices.
The user connects their work account to the personal device,
giving the organisation some identity and management
capabilities while the device remains personally owned.

Entra ID Joined is mainly for corporate-owned devices. The
device becomes joined directly to Microsoft Entra ID and can
be managed more fully through Intune. It is especially useful
for cloud-first organisations that don't need traditional
on-premises Active Directory.

So, if an employee brings their own laptop, I would typically
use Entra ID Registered. If the company provides the laptop
and wants full organisational management, I would typically
use Entra ID Joined.

==================================================
WRONG ANSWERS FROM PRACTICE QUESTIONS
==================================================

Q: [paste the question you got wrong]

Correct answer: [answer]

Why I got it wrong: [honest reason]

What I now know: [correct understanding]