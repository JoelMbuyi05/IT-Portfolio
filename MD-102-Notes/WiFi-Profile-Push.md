# Day 16 — Wi-Fi and Network Profile Push

Date: 23 August 2026
Source:
- Microsoft Learn — "Add Wi-Fi settings for Windows devices in Intune"

==================================================
WHAT I LEARNED TODAY
==================================================

Today I learned how Microsoft Intune can centrally push Wi-Fi
and VPN configuration to managed Windows devices.

Instead of requiring users to manually configure corporate
Wi-Fi, IT can create a configuration profile in Intune and
assign it to company devices.

The device receives the profile and can automatically connect
to the configured corporate network.

==================================================
WHY WI-FI PROFILES ARE USEFUL
==================================================

Without Intune:

User receives laptop
→ Finds Wi-Fi
→ Selects company network
→ Enters credentials/settings
→ Connects manually

With Intune:

IT creates Wi-Fi profile
→ Assigns profile to devices
→ Device receives profile
→ Device automatically connects

This makes deployment faster and reduces configuration errors.

==================================================
KEY WI-FI CONCEPTS
==================================================

SSID
→ The name used to identify a wireless network.

Wi-Fi type
→ Defines the type of wireless configuration.

WLAN Connection Mode
→ Determines how Windows connects to wireless networks.

Auto Connect
→ Allows the device to automatically connect when the
  configured network is available.

WPA2-Enterprise
→ Enterprise Wi-Fi security method commonly used with
  organisational authentication.

EAP
→ Extensible Authentication Protocol.
→ Used to provide authentication for enterprise wireless
  networks.

PEAP
→ Protected Extensible Authentication Protocol.
→ Commonly used for enterprise Wi-Fi authentication.

==================================================
SETTINGS CATALOG VS WI-FI TEMPLATE
==================================================

Settings Catalog
→ Allows individual Wi-Fi-related settings to be configured.

Example:

Allow Internet Sharing:
Blocked

WLAN Connection Mode:
Auto Connect

Wi-Fi Template
→ Provides a more complete Wi-Fi configuration designed
  specifically for connecting devices to a wireless network.

Example:

Network:
XYZ-Corporate

SSID:
XYZ-Corporate

Security:
WPA2-Enterprise

EAP:
PEAP

==================================================
INTERNET SHARING
==================================================

I configured:

Allow Internet Sharing:
Blocked

This prevents users from using the Windows device as an
Internet connection-sharing/hotspot mechanism when the
organisation does not permit it.

==================================================
VPN PROFILES
==================================================

I also learned that Intune can push VPN configuration to
managed devices.

A VPN profile can define things such as:

- VPN provider
- Connection name
- Connection settings
- Authentication requirements
- Connection behaviour

Example:

VPN provider:
Microsoft Tunnel

Connection name:
XYZ-VPN

A VPN profile by itself does not create a complete VPN
infrastructure.

A real deployment also requires the appropriate VPN gateway,
server/infrastructure and authentication configuration.

==================================================
WHAT CONFUSED ME
==================================================

I initially thought creating a VPN profile in Intune would
automatically create the VPN connection infrastructure.

I now understand that Intune can configure the client side,
but the organisation still needs a working VPN service or
gateway for the connection to actually work.

==================================================
HOW THIS CONNECTS TO THE JOB
==================================================

If a company has hundreds of laptops, IT does not want every
employee manually entering Wi-Fi and VPN settings.

Intune can automatically provide the required configuration.

For example:

New laptop
→ Entra ID Join
→ Intune enrollment
→ Wi-Fi profile
→ VPN profile
→ Applications
→ Security policies

This makes the laptop much closer to a ready-to-use corporate
device immediately after deployment.

==================================================
EXAM TIPS
==================================================

Remember:

SSID
→ Name of the wireless network.

WLAN Auto Connect
→ Automatically connects to configured network.

WPA2-Enterprise
→ Enterprise Wi-Fi security.

PEAP
→ EAP authentication method.

Wi-Fi configuration profile
→ Pushes wireless settings to devices.

VPN configuration profile
→ Configures the VPN client.

Important:
Intune configures the client; it does not magically create the
organisation's entire VPN infrastructure.

==================================================
WRONG ANSWERS FROM PRACTICE QUESTIONS
==================================================

Q: [paste question]

Correct answer: [answer]

Why I got it wrong: [honest reason]

What I now know: [correct understanding]