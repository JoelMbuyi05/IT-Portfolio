# Lab 009 — Windows Autopilot Hardware Hash

Date: 17 August 2026
Day: 10 of 30-day MD-102 plan

==================================================
GOAL
==================================================

Understand how Windows Autopilot identifies devices using
hardware information and how devices are registered and
configured through Microsoft Intune.

==================================================
ENVIRONMENT
==================================================

- Windows 10 Lab VM — Win10-Lab1
- VirtualBox
- PowerShell
- Microsoft Intune admin center
- Microsoft 365 E5 tenant

==================================================
TASK 1 — ATTEMPT TO CAPTURE HARDWARE HASH
==================================================

1. Opened PowerShell as Administrator.

2. Attempted to install the Autopilot information script:

Install-Script -Name Get-WindowsAutopilotInfo -Force

3. Attempted to collect and upload the device information:

Get-WindowsAutopilotInfo -Online

Result:

[Record actual result.]

==================================================
IF THE VM FAILED
==================================================

The hardware hash collection may not work correctly in a
VirtualBox VM because Windows Autopilot hardware identification
is designed primarily around physical devices.

If the command failed because of the VM environment, I
documented the failure instead of spending excessive time
trying to force the VM to behave like physical hardware.

Error/message:

[Record exact error.]

Conclusion:

The lab VM was not suitable for reliably demonstrating physical
hardware hash collection.

==================================================
TASK 2 — EXAMINE THE AUTOPILOT CSV TEMPLATE
==================================================

1. Opened:

intune.microsoft.com

2. Navigated to:

Devices
→ Enroll devices
→ Windows enrollment
→ Windows Autopilot devices

3. Selected:

Import

4. Downloaded/examined the CSV template.

Important fields observed:

- Serial Number
- Windows Product ID
- Hardware Hash

==================================================
TASK 3 — UNDERSTAND THE REAL HARDWARE PROCESS
==================================================

Because the lab VM may not provide a usable hardware hash, I
documented the real-world process.

Real-world workflow:

Physical Windows computer
        ↓
Collect hardware information
        ↓
Obtain hardware hash
        ↓
Import device into Autopilot
        ↓
Assign device/profile
        ↓
Configure Intune policies/apps
        ↓
Ship device
        ↓
User connects to Internet
        ↓
Windows OOBE
        ↓
Autopilot identifies device
        ↓
Organisation configuration is applied

==================================================
TASK 4 — EXPLORE AUTOPILOT DEVICES
==================================================

Opened:

Intune
→ Devices
→ Windows
→ Windows Autopilot devices

Explored the available information and checked what a
registered Autopilot device looks like.

Information examined:

- Device name
- Serial number
- Manufacturer
- Model
- Profile assignment
- Group assignment
- Deployment status
- Registration information

Result:

[Record what your tenant displayed.]

==================================================
WHAT BROKE
==================================================

Possible issue:

The hardware hash collection command did not work correctly
inside the VirtualBox VM.

==================================================
HOW I HANDLED IT
==================================================

Instead of spending excessive time trying to collect a physical
hardware hash from a virtual machine, I moved to the Intune
Autopilot import workflow and examined the CSV requirements.

I then documented how the process would work with real
physical hardware.


==================================================
LESSONS LEARNED
==================================================

I learned that Windows Autopilot uses hardware information to
identify organisation-owned Windows devices.

The hardware hash is important because it allows Microsoft to
recognise the device during Windows setup and apply the
organisation's Autopilot configuration.

I also learned that collecting a hardware hash is more
meaningful on physical hardware than inside a VirtualBox VM.

==================================================
EXAM CONNECTION
==================================================

This lab reinforces:

- Windows Autopilot
- Hardware hash
- Device registration
- Autopilot profiles
- Windows OOBE
- Intune
- Device provisioning
- CSV device import
- Serial number
- Windows Product ID
- Hardware identification

==================================================
REAL JOB CONNECTION
==================================================

If my company purchases 100 Windows laptops, manually
configuring every device would take a significant amount of
time.

With Autopilot, IT can register the devices, assign profiles
and configure Intune policies before deployment.

The employee can receive the laptop, connect it to the
Internet and go through Windows setup.

Autopilot then identifies the device and applies the
organisation's configuration.

This makes Windows deployment much more scalable.

==================================================
FINAL RESULT
==================================================

I attempted to collect a hardware hash from the Win10-Lab1 VM.

Because the VM environment may not provide a reliable physical
hardware identity, I also examined the Autopilot CSV import
process and documented the real-world physical-device workflow.

I now understand what the hardware hash is, why it is needed,
how devices are registered with Autopilot, and how Autopilot
works together with Intune during Windows deployment.