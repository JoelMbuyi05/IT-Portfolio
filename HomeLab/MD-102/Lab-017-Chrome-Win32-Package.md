# Lab 017 — Google Chrome Win32 Package

Date: 26 August 2026
Day: 19 of 30-day MD-102 plan

==================================================
GOAL
==================================================

Package Google Chrome as a Win32 application and deploy it
through Microsoft Intune.

The goal is to understand the complete enterprise application
deployment process:

Installer
→ Packaging
→ Intune upload
→ Install command
→ Uninstall command
→ Detection rule
→ Assignment
→ Deployment verification

==================================================
ENVIRONMENT
==================================================

- Microsoft 365 E5 tenant
- Microsoft Intune
- Win10-Lab1
- Windows 10
- Visual Studio Code / Command Prompt
- IntuneWinAppUtil.exe

==================================================
TASK 1 — DOWNLOAD CHROME ENTERPRISE
==================================================

Downloaded the Google Chrome Enterprise MSI installer.

Saved it as:

googlechromestandaloneenterprise64.msi

==================================================
TASK 2 — CREATE PACKAGING FOLDERS
==================================================

Created:

C:\AppPackaging\

Inside it:

C:\AppPackaging\Chrome\

C:\AppPackaging\Output\

Placed the Chrome MSI inside:

C:\AppPackaging\Chrome\

Final structure:

C:\AppPackaging\
    Chrome\
        googlechromestandaloneenterprise64.msi
    Output\

==================================================
TASK 3 — DOWNLOAD INTUNEWINAPPUTIL
==================================================

Downloaded:

IntuneWinAppUtil.exe

This is Microsoft's Win32 Content Prep Tool.

Placed it in a convenient location for running the packaging
process.

==================================================
TASK 4 — PACKAGE CHROME
==================================================

Opened Command Prompt.

Ran:

IntuneWinAppUtil.exe -c "C:\AppPackaging\Chrome" -s "googlechromestandaloneenterprise64.msi" -o "C:\AppPackaging\Output"

Explanation:

-c
→ Specifies the source/content folder.

-s
→ Specifies the setup file.

-o
→ Specifies the output folder.

The tool created a packaged:

.intunewin

file.

Expected:

C:\AppPackaging\Output\

    Chrome.intunewin

==================================================
TASK 5 — ADD WIN32 APP TO INTUNE
==================================================

Opened:

Intune admin center

Navigated to:

Apps
→ Windows
→ Add

Selected:

Windows app (Win32)

Uploaded:

Chrome.intunewin

==================================================
TASK 6 — APPLICATION INFORMATION
==================================================

Configured:

Name:
Google Chrome Enterprise

Publisher:
Google LLC

Version:
[version used in the lab]

Description:
Google Chrome Enterprise browser for XYZ Technology Solutions.

==================================================
TASK 7 — INSTALL COMMAND
==================================================

Configured:

msiexec /i "googlechromestandaloneenterprise64.msi" /quiet /norestart

Purpose:

Install Chrome silently without requiring normal user
interaction.

==================================================
TASK 8 — UNINSTALL COMMAND
==================================================

Configured the appropriate MSI uninstall command.

Example:

msiexec /x {PRODUCT-CODE} /quiet /norestart

IMPORTANT:

Verified the actual MSI product code rather than assuming the
example product code is correct for every Chrome version.

==================================================
TASK 9 — INSTALL BEHAVIOR
==================================================

Configured:

Install behavior:
System

Purpose:

Allow Intune to install Chrome using the device/system context.

==================================================
TASK 10 — DETECTION RULE
==================================================

Created a registry detection rule.

Configured:

Rule type:
Registry

Key path:

HKEY_LOCAL_MACHINE\SOFTWARE\Google\Chrome

Value name:

Version

Detection method:

Key exists

Purpose:

Allow Intune to determine whether Chrome is already installed.

==================================================
TASK 11 — ASSIGN APPLICATION
==================================================

Assigned:

Google Chrome Enterprise

Assignment type:

Required

Target:

All Devices

Purpose:

Automatically install Chrome on assigned Windows devices.

==================================================
TASK 12 — VERIFY DEPLOYMENT
==================================================

On Win10-Lab1:

Triggered an Intune synchronization.

Then checked:

Intune
→ Apps
→ Windows
→ Google Chrome Enterprise
→ Device install status

Possible results:

Installed
Pending
Failed
Not applicable

==================================================
TASK 13 — VERIFY CHROME ON WINDOWS
==================================================

Checked Win10-Lab1.

Verified whether Google Chrome was installed.

Checked:

Start Menu
→ Google Chrome

Also checked:

Settings
→ Apps
→ Installed apps

Expected:

Google Chrome should appear as an installed application.

==================================================
TASK 14 — VERIFY DETECTION
==================================================

Checked whether the registry detection path exists:

HKEY_LOCAL_MACHINE\SOFTWARE\Google\Chrome

Verified that the Chrome version information exists.

This allows Intune to recognise that the application has been
installed.

==================================================
WHAT BROKE
==================================================

Possible problems:

- IntuneWinAppUtil failed.
- .intunewin file was not created.
- Application upload failed.
- Install command was incorrect.
- MSI product code was incorrect.
- Detection rule did not detect Chrome.
- Application remained Pending.
- Application installation failed.
- Chrome installed manually but Intune did not detect it.
- Device did not synchronize with Intune.

==================================================
HOW I FIXED IT
==================================================

Troubleshooting process:

1. Checked the .intunewin package.
2. Confirmed the correct MSI was included.
3. Checked the install command.
4. Checked the uninstall command.
5. Verified the installation context.
6. Checked the detection rule.
7. Confirmed the device was assigned the application.
8. Triggered an Intune synchronization.
9. Checked the Intune device installation status.
10. Checked Windows for the installed application.

==================================================
LESSONS LEARNED
==================================================

I learned that deploying a Windows application through Intune
requires more than simply uploading an installer.

The application must be packaged correctly and Intune must know:

- What application is being installed
- How to install it
- How to uninstall it
- How to detect whether it is installed
- Which users/devices should receive it

The detection rule is particularly important because it allows
Intune to determine the application's installation state.

==================================================
EXAM CONNECTION
==================================================

This lab reinforces:

- Win32 apps
- .intunewin packages
- IntuneWinAppUtil
- MSI installers
- msiexec
- Install commands
- Uninstall commands
- Detection rules
- Registry detection
- System installation
- Required assignments
- Application deployment status
- Intune application troubleshooting

==================================================
REAL JOB CONNECTION
==================================================

A company may need to deploy the same application to hundreds
of Windows devices.

Instead of manually installing the application:

IT packages the application
        ↓
Uploads it to Intune
        ↓
Creates installation commands
        ↓
Creates detection rules
        ↓
Assigns application
        ↓
Intune deploys it
        ↓
IT monitors deployment status

If some devices fail, the technician can investigate the
specific device and determine whether the problem is with:

- Intune assignment
- Application package
- Installation command
- Permissions
- Detection rule
- Device state
- Network connectivity

==================================================
FINAL RESULT
==================================================

Created a Win32 application package for:

Google Chrome Enterprise

Packaged the MSI into an .intunewin file using
IntuneWinAppUtil.

Uploaded the package to Intune and configured:

- Application information
- Install command
- Uninstall command
- System installation
- Registry detection
- Required assignment

Verified the deployment and documented the installation status
on Win10-Lab1.