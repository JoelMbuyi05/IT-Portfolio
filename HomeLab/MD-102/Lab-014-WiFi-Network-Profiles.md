# Lab 014 — Wi-Fi and Network Profile Push

Date: 23 August 2026
Day: 16 of 30-day MD-102 plan

==================================================
GOAL
==================================================

Create Intune Wi-Fi and VPN configuration profiles and
understand how network settings can be automatically pushed to
managed Windows devices.

==================================================
ENVIRONMENT
==================================================

- Microsoft 365 E5 tenant
- Microsoft Intune
- Microsoft Entra ID
- Win10-Lab1
- Windows 10 and later
- Intune Configuration Profiles

==================================================
TASK 1 — WI-FI SETTINGS CATALOG PROFILE
==================================================

1. Opened:

Intune admin center

2. Navigated to:

Devices
→ Configuration profiles
→ Create profile

3. Selected:

Platform:
Windows 10 and later

Profile type:
Settings catalog

4. Created:

Name:
XYZ-WiFi-Security

==================================================
CONFIGURED SETTINGS
==================================================

Searched for:

Wi-Fi

Configured:

Allow Internet Sharing:
Blocked

WLAN Connection Mode:
Auto Connect

Purpose:

Prevent Internet sharing while allowing Windows to
automatically connect to configured wireless networks.

==================================================
TASK 2 — CREATE WI-FI PROFILE
==================================================

Created another configuration profile specifically for the
corporate wireless network.

Navigated to:

Devices
→ Configuration profiles
→ Create profile

Selected:

Platform:
Windows 10 and later

Profile type:
Templates
→ Wi-Fi

==================================================
WI-FI CONFIGURATION
==================================================

Profile name:

XYZ-Corporate-WiFi

Configured:

Wi-Fi type:
Enterprise

Network name:
XYZ-Corporate

SSID:
XYZ-Corporate

Connect automatically:
Yes

Security type:
WPA2-Enterprise

EAP type:
PEAP

Purpose:

The device receives the corporate wireless configuration from
Intune instead of requiring the user to manually configure the
network.

==================================================
IMPORTANT NOTE ABOUT PASSWORDS / AUTHENTICATION
==================================================

A corporate Wi-Fi profile does not necessarily mean that a
normal Wi-Fi password is simply stored and pushed to every
device.

With WPA2-Enterprise and PEAP, authentication is normally based
on organisational credentials or another enterprise
authentication mechanism.

The actual authentication infrastructure must also exist.

Therefore:

Intune Wi-Fi profile
→ Configures the Windows Wi-Fi client

RADIUS/802.1X authentication infrastructure
→ Authenticates the user/device

Both sides are required for a real enterprise deployment.

==================================================
TASK 3 — ASSIGN WI-FI PROFILE
==================================================

Assigned:

XYZ-Corporate-WiFi

To:

[Device group / All Devices]

Purpose:

Ensure the appropriate corporate devices receive the Wi-Fi
configuration.

==================================================
TASK 4 — CREATE VPN PROFILE
==================================================

Navigated to:

Devices
→ Configuration profiles
→ Create profile

Selected:

Platform:
Windows 10 and later

Profile type:
VPN

Created:

Name:
XYZ-VPN

Configured:

VPN provider:
Microsoft Tunnel / available provider

Connection name:
XYZ-VPN

==================================================
VPN OBSERVATION
==================================================

The VPN profile defines how the Windows device should be
configured to connect to the VPN.

However, the lab does not have a complete production VPN
gateway/infrastructure.

Therefore, I did not treat the VPN profile as a complete working
VPN deployment.

A real implementation would require:

- VPN gateway/server
- Authentication
- Network routing
- DNS configuration
- Appropriate certificates or credentials where required
- Firewall/network configuration

==================================================
TASK 5 — ASSIGN VPN PROFILE
==================================================

Assigned:

XYZ-VPN

To:

[Device group]

Result:

[Record result.]

==================================================
TASK 6 — SYNC DEVICE
==================================================

On Win10-Lab1, triggered an Intune synchronization.

Used:

Settings
→ Accounts
→ Access work or school
→ Work/school account
→ Info
→ Sync

Alternatively, the sync can be triggered from the Intune admin
center.

==================================================
TASK 7 — VERIFY DEPLOYMENT
==================================================

In Intune, checked:

Devices
→ Configuration profiles
→ XYZ-Corporate-WiFi
→ Device status

Checked whether Win10-Lab1 showed:

Succeeded
Pending
Error
Conflict

Actual result:

[Record result.]

==================================================
TASK 8 — VERIFY LOCAL DEVICE
==================================================

On Win11-Lab1, checked Windows Wi-Fi settings.

Expected:

XYZ-Corporate should appear as a configured wireless network.

If the device is within range of a real network matching the
profile and the authentication infrastructure is available,
the device should be able to connect automatically.

Actual result:

[Record result.]

Because this home lab does not necessarily contain a real
XYZ-Corporate enterprise Wi-Fi network, the profile may be
successfully deployed without the VM actually establishing a
wireless connection.

==================================================
WHAT BROKE
==================================================

Possible issues:

- Profile remained Pending.
- Profile showed an error.
- Wi-Fi profile was successfully deployed but no matching
  network existed.
- PEAP authentication could not be tested.
- VPN profile deployed but could not establish a connection.
- Device was not included in the assignment.

==================================================
HOW I FIXED IT
==================================================

Troubleshooting process:

1. Confirmed the device was enrolled in Intune.
2. Confirmed the device was included in the assignment.
3. Checked profile deployment status.
4. Triggered an Intune synchronization.
5. Checked for conflicting configuration profiles.
6. Checked Windows Wi-Fi settings.
7. Confirmed whether the actual network existed.
8. Confirmed whether enterprise authentication infrastructure
   was available.

==================================================
LESSONS LEARNED
==================================================

I learned that Intune can centrally configure network settings
on managed Windows devices.

Wi-Fi profiles can automatically configure corporate wireless
settings, reducing the need for users to manually configure
their devices.

I also learned that Intune configuration is only one part of an
enterprise network.

For WPA2-Enterprise Wi-Fi, the organisation still needs the
appropriate authentication infrastructure.

Similarly, creating a VPN profile does not create the actual
VPN infrastructure.

==================================================
EXAM CONNECTION
==================================================

This lab reinforces:

- Intune Wi-Fi profiles
- Settings Catalog
- Wi-Fi templates
- SSID
- WLAN connection mode
- Auto Connect
- WPA2-Enterprise
- PEAP
- VPN profiles
- Configuration profile assignments
- Device synchronization
- Profile deployment status
- Enterprise network authentication

==================================================
REAL JOB CONNECTION
==================================================

Imagine a company gives 200 employees new laptops.

Instead of asking every employee to manually configure:

- Corporate Wi-Fi
- VPN
- Security settings
- Browser settings
- Password policies

IT can configure these centrally in Intune.

The deployment can become:

Autopilot
→ Intune enrollment
→ Wi-Fi profile
→ VPN profile
→ Security configuration
→ Applications
→ Compliance policies

This creates a much more consistent and scalable deployment
process.

==================================================
FINAL RESULT
==================================================

Created:

1. XYZ-WiFi-Security
2. XYZ-Corporate-WiFi
3. XYZ-VPN

Configured and assigned the profiles to the appropriate
devices/groups and reviewed their deployment status.

I now understand how Intune can push network configuration to
managed Windows devices and the difference between configuring
a network client through Intune and providing the actual
network infrastructure behind it.