# Lab 015 — Printer Mapping with PowerShell

Date: 24 August 2026
Day: 17 of 30-day MD-102 plan

==================================================
GOAL
==================================================

Create a PowerShell script that configures a network printer
and deploy the script to Windows devices through Microsoft
Intune.

The objective is to practice enterprise automation and
understand how Intune can distribute PowerShell scripts to
managed Windows devices.

==================================================
ENVIRONMENT
==================================================

- Microsoft 365 E5 tenant
- Microsoft Intune
- Microsoft Entra ID
- Win10-Lab1
- Windows PowerShell
- Visual Studio Code

==================================================
TASK 1 — CREATE THE POWERSHELL SCRIPT
==================================================

Opened Visual Studio Code.

Created:

MapPrinters.ps1

Script:

# Map network printer for XYZ Technology Solutions
$PrinterIP = "192.168.1.100"
$PrinterName = "XYZ-Office-Printer"

# Add printer port
Add-PrinterPort -Name "IP_$PrinterIP" -PrinterHostAddress $PrinterIP

# Add printer using the port
Add-Printer -Name $PrinterName `
            -DriverName "Generic / Text Only" `
            -PortName "IP_$PrinterIP"

Write-Host "Printer $PrinterName mapped successfully"

==================================================
TASK 2 — UNDERSTAND THE SCRIPT
==================================================

The script first defines:

Printer IP:
192.168.1.100

Printer name:
XYZ-Office-Printer

It then creates a printer port:

IP_192.168.1.100

The printer is then added using:

Generic / Text Only

The printer is connected to the created port.

Finally, PowerShell displays:

Printer XYZ-Office-Printer mapped successfully

==================================================
TASK 3 — TEST THE SCRIPT LOCALLY
==================================================

Before deploying through Intune, the script should ideally be
tested locally on Win10-Lab1.

Opened PowerShell as Administrator.

Executed:

.\MapPrinters.ps1

Then checked installed printers:

Get-Printer

Checked printer ports:

Get-PrinterPort

Expected:

XYZ-Office-Printer should appear if the required printer port
and driver configuration are valid.

Actual result:

[Record actual result.]

==================================================
IMPORTANT LAB LIMITATION
==================================================

If 192.168.1.100 is not a real reachable printer in the lab,
the printer cannot actually print.

The purpose of the exercise is to understand the automation
and Intune deployment process.

If the Generic / Text Only driver is available, Windows may
create the printer object even though no physical printer
exists at the configured IP.

==================================================
TASK 4 — UPLOAD SCRIPT TO INTUNE
==================================================

Opened:

Intune admin center

Navigated to:

Devices
→ Scripts
→ Add
→ Windows 10 and later

Created:

Name:
XYZ-Map-Office-Printer

Uploaded:

MapPrinters.ps1

Configured:

Run script in 64-bit PowerShell:
Yes

Run this script using the logged-on credentials:
No

The script therefore runs using the device/system context.

==================================================
TASK 5 — ASSIGN SCRIPT
==================================================

Assigned the script to:

All Devices

Purpose:

Deploy the printer configuration to the assigned Windows
devices.

==================================================
TASK 6 — VERIFY INTUNE DEPLOYMENT
==================================================

Navigated to:

Devices
→ Scripts
→ XYZ-Map-Office-Printer

Checked device execution status.

Possible states include:

Pending
Succeeded
Failed

Actual status:

[Record actual result.]

==================================================
TASK 7 — VERIFY WIN10-LAB1
==================================================

On Win10-Lab1:

Opened PowerShell.

Ran:

Get-Printer

Expected:

XYZ-Office-Printer

Also checked:

Get-PrinterPort

Expected:

IP_192.168.1.100

Actual result:

[Record result.]

==================================================
WHAT BROKE
==================================================

Possible problems:

- Script failed to execute.
- Printer driver was unavailable.
- Printer IP was unreachable.
- Printer port already existed.
- Script was not assigned correctly.
- Intune device was not synchronized.
- PowerShell execution failed.
- Printer appeared but could not actually print.

==================================================
HOW I FIXED IT
==================================================

Troubleshooting process:

1. Confirmed the device was enrolled in Intune.
2. Confirmed the script was assigned to the device.
3. Checked Intune script status.
4. Triggered an Intune synchronization.
5. Checked PowerShell/script execution.
6. Checked Get-Printer.
7. Checked Get-PrinterPort.
8. Verified the printer IP.
9. Verified the required driver.
10. Checked network connectivity to the printer.

==================================================
LESSONS LEARNED
==================================================

I learned how PowerShell and Intune can be combined to automate
Windows administration tasks.

Instead of manually installing a printer on every computer,
IT can deploy a PowerShell script through Intune.

I also learned that successful script deployment does not
necessarily mean that the underlying task will work.

The device still needs:

- Correct network connectivity
- Correct printer IP
- Correct driver
- Appropriate permissions
- A functioning printer

==================================================
EXAM CONNECTION
==================================================

This lab reinforces:

- Intune PowerShell scripts
- Windows device management
- Script assignments
- System context
- 64-bit PowerShell
- Device synchronization
- Script deployment status
- Enterprise automation
- Printer management

==================================================
REAL JOB CONNECTION
==================================================

In an enterprise environment, IT can use Intune to automate
repetitive tasks across hundreds or thousands of Windows
devices.

For example:

New employee receives laptop
        ↓
Autopilot provisions device
        ↓
Intune enrolls device
        ↓
PowerShell scripts execute
        ↓
Corporate printer configured
        ↓
Required applications installed
        ↓
Security policies applied

This reduces manual work and creates a consistent deployment
process.

==================================================
FINAL RESULT
==================================================

Created:

MapPrinters.ps1

Created an Intune PowerShell deployment:

XYZ-Map-Office-Printer

Assigned it to the appropriate devices and verified the
deployment status.

The lab demonstrated how Intune can use PowerShell to automate
enterprise Windows administration tasks such as printer
configuration.