# Day 11 — Autopilot Deployment Profiles

Date: 18 August 2026
Source: Microsoft Learn — "Windows Autopilot deployment profiles"

==================================================
WHAT I LEARNED TODAY
==================================================

Today I learned how Windows Autopilot deployment profiles
control how a Windows device behaves during its initial setup.

An Autopilot deployment profile tells Windows how the device
should be configured during the Out-of-Box Experience (OOBE).

I learned four important deployment scenarios:

1. User-Driven
2. Self-Deploying
3. Pre-Provisioning (White Glove)
4. Existing Devices

==================================================
1. USER-DRIVEN
==================================================

User-Driven is the most common deployment mode for normal
employees.

The employee receives the company computer, connects it to the
Internet and signs in with their work account.

Autopilot then:

- Joins the device to Entra ID
- Enrolls it into Intune
- Applies configuration policies
- Installs required applications
- Configures the device for the employee

This is suitable for standard corporate employee laptops.

==================================================
2. SELF-DEPLOYING
==================================================

Self-Deploying is designed for situations where there may be
little or no user interaction during deployment.

The device can automatically:

- Join Entra ID
- Enroll into Intune
- Apply policies
- Install required configuration

Typical examples include:

- Kiosks
- Shared devices
- Digital signage

==================================================
3. PRE-PROVISIONING / WHITE GLOVE
==================================================

Pre-Provisioning allows IT to prepare the device before
giving it to the employee.

IT can configure:

- Applications
- Policies
- Security settings
- Device configuration

The employee receives a device that is already mostly
prepared.

The user then signs in and completes the remaining user-specific
configuration.

This is useful when an organisation wants employees to receive
a ready-to-use computer.

==================================================
4. EXISTING DEVICES
==================================================

Existing Devices is used for computers that are already in use
and need to be moved into an Autopilot deployment process.

It can be used when an organisation wants to redeploy or
reconfigure existing Windows devices rather than treating them
as completely new devices.

==================================================
KEY CONCEPTS
==================================================

Autopilot Deployment Profile
→ Defines how a Windows device should be configured during
  deployment.

OOBE
→ Windows Out-of-Box Experience.

User-Driven
→ Employee participates in setup.

Self-Deploying
→ Minimal/no user interaction.

Pre-Provisioning
→ IT prepares the device before giving it to the employee.

Existing Devices
→ Used for redeploying/configuring existing Windows devices.

Enrollment Status Page (ESP)
→ Shows deployment progress and can prevent the user from
  using the device until required configuration/apps are
  installed.

==================================================
WHY THE ENROLLMENT STATUS PAGE MATTERS
==================================================

The Enrollment Status Page helps ensure that the device is
properly configured before the employee starts using it.

For example, an organisation may require:

- Microsoft 365 applications
- Security software
- Configuration policies
- Company applications

The ESP can display installation progress and prevent the user
from accessing the desktop until required applications and
configuration have been installed.

==================================================
HOW THIS CONNECTS TO THE JOB
==================================================

As an IT technician, I may need to prepare dozens or hundreds
of Windows laptops.

Instead of manually configuring every computer, I can use
Autopilot deployment profiles to standardise the deployment
process.

For example:

Normal employee:
→ User-Driven

Kiosk:
→ Self-Deploying

VIP/new employee laptop:
→ Pre-Provisioning

Existing company computers being redeployed:
→ Existing Devices

==================================================
WHAT CONFUSED ME
==================================================

At first I thought Autopilot was simply another way of
installing Windows.

I now understand that Autopilot is more about controlling and
automating the provisioning experience and connecting the
device to Microsoft cloud management services such as Entra ID
and Intune.

==================================================
EXAM TIPS
==================================================

Remember the scenarios:

User-Driven
→ Normal employee

Self-Deploying
→ Kiosk/shared/signage

Pre-Provisioning
→ IT prepares device before user receives it

Existing Devices
→ Existing Windows devices being redeployed/configured

Also remember:

Autopilot Profile
→ Defines deployment behaviour.

Enrollment Status Page
→ Controls/displays deployment progress.

==================================================
DEFEND QUESTION
==================================================

Question:

"Why use Autopilot instead of imaging? Walk me through the
difference."

Answer:

Traditional imaging usually means IT creates a standard
Windows image containing an operating system and potentially
applications and configurations.

That image is then deployed to multiple computers.

Autopilot takes a different approach. Instead of maintaining
and deploying a large custom Windows image, the organisation
uses the normal Windows installation and lets cloud services
such as Intune and Entra ID apply the required configuration,
applications and policies.

With imaging, IT generally manages the image itself.

With Autopilot, IT manages the deployment configuration
centrally.

For example:

Traditional imaging:

Create image
→ Capture image
→ Deploy image
→ Configure device
→ Update/rebuild image when requirements change

Autopilot:

Register device
→ Assign Autopilot profile
→ User starts device
→ Device connects to Internet
→ Autopilot identifies device
→ Entra ID/Intune configuration is applied

Autopilot is especially useful for modern cloud-first
organisations because it reduces manual provisioning and makes
deployment more scalable.

I would still consider the organisation's requirements before
choosing one approach, because traditional imaging can still
be appropriate in certain environments.