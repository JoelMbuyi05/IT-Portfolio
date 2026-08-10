# Mobile Devices

## Connection Types
USB-C     — current standard, charging + data + video
Lightning  — Apple only (older iPhones, being phased out)
Bluetooth  — short range under 10 metres
NFC        — Near Field Communication, tap to pay/pair
Wi-Fi      — wireless network, already covered
Hotspot    — sharing mobile data as Wi-Fi to other devices

## iOS vs Android
iOS    — Apple only, closed ecosystem, updates from Apple directly
Android — multiple manufacturers, open, updates vary by maker

## MDM (Mobile Device Management)
What it is: software that manages phones and tablets remotely
What it can do: push apps, wipe device, enforce passcode, 
track location, block camera
Microsoft Intune is an MDM — you manage it in Week 3+

## MAM vs MDM
MDM — manages the whole device (corporate-owned phones)
MAM — manages only the apps, not the device (personal phones 
with work apps) — better for BYOD

## Common Mobile Support Scenarios
Work email not syncing → remove and re-add account
MFA app not working → re-register authenticator
Device not receiving apps → check Intune enrollment status
Lost/stolen device → remote wipe via Intune immediately