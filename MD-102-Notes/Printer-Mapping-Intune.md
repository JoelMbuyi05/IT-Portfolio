# Day 17 — Enterprise Printer Mapping

Date: 24 August 2026
Source:
- Microsoft Learn — "Use PowerShell scripts on Windows in Intune"

==================================================
WHAT I LEARNED TODAY
==================================================

Today I learned how PowerShell scripts can be deployed through
Microsoft Intune to automate tasks on managed Windows devices.

A useful example is printer mapping.

Instead of manually configuring a printer on every company
computer, IT can deploy a PowerShell script through Intune.

The general process is:

PowerShell script
    ↓
Upload to Intune
    ↓
Assign to devices/users
    ↓
Intune deploys script
    ↓
Windows executes script
    ↓
Printer is configured

==================================================
WHY USE POWERSHELL FOR PRINTER MAPPING?
==================================================

In a small environment, a technician could manually install a
printer.

In an enterprise environment with hundreds of computers, this
would be slow and inconsistent.

PowerShell allows IT to automate the configuration.

For example:

200 computers
    ↓
One PowerShell script
    ↓
Intune deployment
    ↓
Printer configured automatically

==================================================
KEY POWERSHELL COMMANDS
==================================================

Add-PrinterPort
→ Creates a printer port on Windows.

Add-Printer
→ Creates/adds a printer using the specified driver and port.

Write-Host
→ Displays a message in PowerShell.

==================================================
SCRIPT BREAKDOWN
==================================================

The script defines the printer IP:

$PrinterIP = "192.168.1.100"

Then defines the printer name:

$PrinterName = "XYZ-Office-Printer"

The printer port is created:

Add-PrinterPort

The printer is then added:

Add-Printer

The script finally displays a success message.

==================================================
INTUNE SCRIPT SETTINGS
==================================================

When deploying a PowerShell script through Intune, important
settings include:

Run script in 64-bit PowerShell:
Yes

Run this script using the logged-on credentials:
No

Running as the system account means the script executes with
device-level privileges rather than depending on the currently
logged-in user's permissions.

==================================================
IMPORTANT REAL-WORLD CONSIDERATION
==================================================

The example printer uses:

192.168.1.100

That is only a lab/example address.

For the script to successfully install the printer in a real
environment:

- The printer must actually exist.
- The device must be able to reach the printer.
- The printer IP must be correct.
- The required printer driver must exist.
- The selected driver must support the printer.

Therefore, a script can successfully execute while the printer
installation itself can still fail because of incorrect
networking, driver or printer configuration.

==================================================
WHAT CONFUSED ME
==================================================

I initially thought deploying the script through Intune was
enough to guarantee the printer would work.

I now understand that Intune is only delivering/executing the
configuration. The printer, network connectivity and correct
driver must also be available.

==================================================
HOW THIS CONNECTS TO THE JOB
==================================================

A user might say:

"My new laptop doesn't have the office printer."

Instead of manually connecting to the printer, an administrator
can check:

1. Is the device enrolled in Intune?
2. Did the PowerShell script deploy?
3. Did the script execute successfully?
4. Is the printer IP reachable?
5. Is the printer port present?
6. Is the correct driver installed?
7. Does Windows show the printer?

This gives a structured troubleshooting process.

==================================================
EXAM TIPS
==================================================

Remember:

Intune PowerShell scripts
→ Automate configuration/tasks on Windows devices.

Run as logged-on user = No
→ Script runs using system/device context.

64-bit PowerShell = Yes
→ Uses the 64-bit PowerShell environment.

Assignment
→ Determines which users/devices receive the script.

Also remember:

Script deployed successfully
≠
Every action inside the script necessarily succeeded.

Always consider the underlying device, network and permissions.

==================================================
WRONG ANSWERS FROM PRACTICE QUESTIONS
==================================================

Q: [paste question]

Correct answer: [answer]

Why I got it wrong: [honest reason]

What I now know: [correct understanding]