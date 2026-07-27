# Lab-003 — Simulating a Missing Boot Drive

## Goal
Understand what happens when a computer cannot access its boot drive.

## Environment
- Host OS: Windows 11
- Hypervisor: Oracle VirtualBox
- Guest OS: Windows 11
- Storage: Windows11.vdi

## Procedure
1. Powered off the virtual machine.
2. Opened VirtualBox Settings → Storage.
3. Detached the Windows11.vdi virtual hard disk.
4. Started the virtual machine.

## Observations
- The virtual machine powered on.
- Windows did not start because the boot drive was unavailable.
- The VM prompted for Windows installation or another bootable device, indicating no operating system could be found.

## Root Cause
The virtual hard disk containing the Windows installation was detached from the virtual machine. Without a bootable storage device, the system could not locate the operating system.

## Fix Applied
1. Powered off the VM.
2. Reattached the original Windows11.vdi file.
3. Restarted the VM.

## Verification
- Windows booted successfully.
- The operating system loaded normally.

## How I Would Explain This to a User
"Your computer can't find the drive that contains Windows. I'll check whether the storage device is connected correctly and verify that the computer is trying to boot from the correct drive."

## What I Would Check on a Real PC
1. Verify the SSD/HDD is detected in BIOS/UEFI.
2. Check SATA or NVMe connections.
3. Confirm the boot order.
4. Listen for signs of drive failure.
5. Run storage diagnostics if the drive is detected.

## Lessons Learned
- A computer requires a bootable storage device to start Windows.
- If the boot drive is unavailable, the system cannot load the operating system.
- Always verify storage connectivity before assuming Windows is corrupted.