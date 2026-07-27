# TJ-003 — Virtual Machine Failed to Boot Due to Missing Boot Drive

## Environment
- Oracle VirtualBox
- Windows 11 VM

## Symptom
The VM powered on but Windows did not start. Instead, the VM requested Windows installation media because no bootable operating system was available.

## Initial Theory
The boot drive containing Windows was not attached to the virtual machine.

## Was the Theory Correct?
Yes.

## Troubleshooting Steps
1. Opened VM Storage settings.
2. Confirmed the Windows11.vdi file had been detached.
3. Reattached the existing virtual disk.
4. Restarted the VM.

## Root Cause
The virtual hard disk containing Windows was detached.

## Fix
Reattached the existing Windows11.vdi file.

## Verification
The VM booted successfully after the storage device was reattached.

## What I'd Check First Next Time
- Verify the boot drive is attached.
- Check BIOS/UEFI boot order.
- Confirm the drive is detected before troubleshooting Windows.

## Real-World Connection
On a physical computer, similar symptoms can occur if:
- An SSD or HDD has failed.
- A SATA or NVMe connection is loose.
- The BIOS/UEFI boot order is incorrect.
- The boot drive is not detected by the motherboard.