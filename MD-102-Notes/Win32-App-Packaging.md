# Day 19 — Win32 App Packaging

Date: 26 August 2026
Source:
- Microsoft Learn — "Add and assign Win32 apps to Microsoft Intune"

==================================================
WHAT I LEARNED TODAY
==================================================

Today I learned how to package and deploy Windows applications
through Microsoft Intune using the Win32 app format.

Win32 apps are used when an organisation needs to deploy
traditional Windows applications through Intune.

The general process is:

Application installer
        ↓
Package with IntuneWinAppUtil
        ↓
.intunewin file
        ↓
Upload to Intune
        ↓
Configure install/uninstall commands
        ↓
Configure detection rules
        ↓
Assign to devices/users
        ↓
Intune installs application
        ↓
Detection rule verifies installation

==================================================
WHAT IS A WIN32 APP?
==================================================

A Win32 app is a traditional Windows application that can be
packaged and deployed through Microsoft Intune.

Examples:

- Google Chrome
- Adobe applications
- VLC
- 7-Zip
- Company-specific applications
- Line-of-business applications

Intune uses the .intunewin format to package the application
content before deployment.

==================================================
INTUNEWINAPPUTIL
==================================================

IntuneWinAppUtil.exe is Microsoft's Win32 Content Prep Tool.

Its purpose is to take application installation files and
package them into an .intunewin file.

Example:

googlechromestandaloneenterprise64.msi

        ↓

IntuneWinAppUtil

        ↓

Chrome.intunewin

The resulting .intunewin file is uploaded to Intune.

==================================================
INSTALL COMMAND
==================================================

For an MSI application:

msiexec /i "googlechromestandaloneenterprise64.msi" /quiet /norestart

Important options:

/i
→ Install the MSI.

/quiet
→ Performs the installation without displaying normal
  installation prompts.

/norestart
→ Prevents the installer from automatically restarting
  Windows.

==================================================
UNINSTALL COMMAND
==================================================

Example:

msiexec /x {PRODUCT-CODE} /quiet /norestart

/x
→ Uninstalls the MSI.

/quiet
→ Runs silently.

/norestart
→ Prevents an automatic restart.

The actual product code should be verified for the specific
application version rather than blindly assuming it is the
same for every installer.

==================================================
INSTALL BEHAVIOR
==================================================

System

→ The application installs in the device/system context rather
  than requiring the logged-in user to perform the installation.

This is useful for corporate applications that should be
installed automatically on managed company devices.

==================================================
DETECTION RULES
==================================================

Detection rules tell Intune whether the application is already
installed.

This is extremely important.

Intune needs to answer:

"Is this application already installed on this device?"

If the detection rule finds the expected application:

→ Intune considers the app installed.

If it does not:

→ Intune can attempt the installation.

Example:

Registry path:

HKEY_LOCAL_MACHINE\SOFTWARE\Google\Chrome

Value:

Version

Detection method:

Key exists

==================================================
WHY DETECTION MATTERS
==================================================

Without detection, Intune would have difficulty determining
whether an application is already present.

Example:

Device already has Chrome
        ↓
Intune checks detection rule
        ↓
Chrome registry key exists
        ↓
Intune knows Chrome is installed

Detection rules therefore help Intune manage application
installation state.

==================================================
REQUIRED VS AVAILABLE
==================================================

Required:

→ Intune automatically installs the application on assigned
  devices.

Available:

→ The application is offered to the user through the
  Company Portal, allowing the user to install it when needed.

For this lab, Chrome was assigned as:

Required

==================================================
WHAT CONFUSED ME
==================================================

I initially thought uploading the installer to Intune was enough.

I now understand that Intune also needs installation commands,
uninstallation commands, detection rules and assignments to
properly manage the application.

==================================================
HOW THIS CONNECTS TO THE JOB
==================================================

Imagine a company has 500 Windows laptops and wants every
employee to have Chrome.

Instead of manually installing Chrome on every computer:

IT packages Chrome once
        ↓
Uploads it to Intune
        ↓
Assigns it to company devices
        ↓
Intune deploys it automatically

If Chrome is missing from a device, Intune can detect that and
attempt the installation.

==================================================
EXAM TIPS
==================================================

Remember:

.intunewin
→ Packaged Win32 application format.

IntuneWinAppUtil.exe
→ Packages Win32 application content.

Install command
→ Tells Windows how to install the application.

Uninstall command
→ Tells Windows how to remove it.

Detection rule
→ Tells Intune whether the application is installed.

System install behavior
→ Installs in device/system context.

Required assignment
→ Automatically installs the application.

Available assignment
→ Makes the application available to the user through
  Company Portal.

MSI
→ Windows Installer package.

msiexec
→ Windows Installer command-line utility.

==================================================
WRONG ANSWERS FROM PRACTICE QUESTIONS
==================================================

Q: [paste question]

Correct answer: [answer]

Why I got it wrong: [honest reason]

What I now know: [correct understanding]