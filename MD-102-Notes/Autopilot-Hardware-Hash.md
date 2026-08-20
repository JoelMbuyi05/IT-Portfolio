# Day 10 — Autopilot Hardware Hash

Date: 17 August 2026
Source:
- Microsoft Learn — "Set up Windows Autopilot"

==================================================
WHAT I LEARNED TODAY
==================================================

Today I learned about Windows Autopilot and the hardware hash.

Windows Autopilot allows an organisation to prepare and deploy
Windows devices without manually configuring every computer.

The hardware hash is a unique identifier associated with a
Windows device's hardware.

The organisation can register the device with Windows Autopilot
before giving it to the user.

When the device starts Windows and connects to the Internet,
Microsoft can identify the registered device and apply the
organisation's Autopilot configuration.

The basic process is:

Physical device
      ↓
Collect hardware information
      ↓
Hardware hash
      ↓
Register device in Intune/Autopilot
      ↓
Assign Autopilot profile
      ↓
Device shipped to user
      ↓
User starts device
      ↓
Device connects to Internet
      ↓
Microsoft identifies device
      ↓
Autopilot profile is applied

==================================================
HARDWARE HASH
==================================================

The hardware hash acts as a device fingerprint used by
Windows Autopilot to identify a specific device.

It contains hardware-related information that allows Microsoft
to recognise the device during the Windows setup process.

The important point is:

The hardware hash identifies the physical device.

It is not simply the computer's serial number.

==================================================
WHY IT MATTERS
==================================================

Without Autopilot, an IT technician might have to:

- Unbox the computer
- Install/configure Windows
- Create or configure the user
- Install applications
- Configure policies
- Configure security settings
- Join the device to the organisation
- Deliver the computer

With Autopilot, much of this can be configured before the
device reaches the employee.

The organisation can register the device and assign the
appropriate Autopilot profile.

The user can then receive the device, connect it to the
Internet and complete the setup while organisational policies
and configuration are applied.

==================================================
KEY CONCEPTS
==================================================

Windows Autopilot
→ Cloud-based Windows deployment and provisioning technology.

Hardware Hash
→ Hardware-based identifier used to identify a device for
  Autopilot registration.

Autopilot Device Registration
→ Registering the device so Microsoft knows it belongs to the
  organisation.

Autopilot Profile
→ Configuration that determines how Windows should be set up
  for the organisation/user.

OOBE
→ Out-of-Box Experience — the Windows setup experience when
  the user first starts the device.

Intune
→ Used to manage devices and configure policies/applications
  after enrollment.

==================================================
WHAT I DID IN THE LAB
==================================================

I attempted to capture the hardware hash from Win10-Lab1 using
PowerShell.

Command:

Install-Script -Name Get-WindowsAutopilotInfo -Force

Then:

Get-WindowsAutopilotInfo -Online

Result:

If the VM could not provide the required information, I did
not spend excessive time troubleshooting the VirtualBox
environment because hardware hash collection is primarily
intended for physical devices.

==================================================
AUTOPILOT CSV IMPORT
==================================================

I opened:

intune.microsoft.com

Then navigated to:

Devices
→ Enroll devices
→ Windows enrollment
→ Windows Autopilot devices
→ Import

I downloaded/examined the CSV template.

Important fields included:

- Serial Number
- Windows Product ID
- Hardware Hash

I learned that these details are used when manually importing
devices into Windows Autopilot.

==================================================
REAL-WORLD PROCESS
==================================================

In a real IT environment, the process would normally be:

1. Obtain the physical Windows device.

2. Start the device or use an appropriate provisioning
   process.

3. Collect the device's hardware information/hardware hash.

4. Upload/import the device into Windows Autopilot.

5. Assign the appropriate Autopilot deployment profile.

6. Configure required applications, policies and settings
   through Intune.

7. Ship the device to the employee.

8. Employee starts the device.

9. Employee connects the device to the Internet.

10. Windows contacts Microsoft's services.

11. The device is recognised as an organisation-owned
    Autopilot device.

12. The assigned Autopilot configuration is applied.

==================================================
INTUNE AUTOPILOT DEVICES
==================================================

I explored:

Intune
→ Devices
→ Windows
→ Windows Autopilot devices

I checked what information is available for registered
Autopilot devices.

Information can include:

- Device name
- Serial number
- Manufacturer
- Model
- Group assignment
- Profile assignment
- Deployment status
- Registration information

==================================================
WHAT CONFUSED ME
==================================================

At first I thought the hardware hash was simply another name
for the device serial number.

I now understand that the serial number is only one piece of
device information. The hardware hash contains additional
hardware-related information used to identify the device for
Autopilot.

==================================================
HOW THIS CONNECTS TO THE JOB
==================================================

Autopilot is useful when an organisation purchases many
Windows computers.

Instead of IT manually configuring every computer, the
organisation can register the devices with Autopilot and
configure the deployment process centrally.

This allows IT technicians to prepare devices before they
reach employees.

If an employee receives a new company laptop, they can
potentially complete the Windows setup themselves while
Autopilot and Intune automatically apply the organisation's
configuration.

==================================================
EXAM TIPS
==================================================

Remember:

Hardware hash
→ Identifies the device for Autopilot.

Autopilot
→ Helps automate Windows deployment.

Autopilot profile
→ Defines how the device should be configured during
  deployment.

Intune
→ Provides management, policies, applications and compliance.

OOBE
→ Windows setup experience where Autopilot can take effect.

Important:

Hardware hash ≠ serial number.

The serial number is one identifying attribute, while the
hardware hash contains more hardware-related information.

==================================================
WRONG ANSWERS FROM PRACTICE QUESTIONS
==================================================

Q: [paste question]

Correct answer: [answer]

Why I got it wrong: [honest reason]

What I now know: [correct understanding]