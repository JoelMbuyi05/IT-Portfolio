# Lab-001 — Installing Windows 11 in a Virtual Machine

## Date

25 July 2026

## Goal

Install Windows 11 inside Oracle VirtualBox and prepare a working virtual machine for IT Support labs and troubleshooting exercises.

## Environment

- Host OS: Windows 11
- Hypervisor: Oracle VirtualBox
- Guest OS: Windows 11
- Installation Media: Windows 11 ISO
- Storage: Virtual Hard Disk (VDI)

---

# Objective

Create a Windows 11 virtual machine from scratch and complete the operating system installation.

---

# Procedure

### Step 1 — Create a New Virtual Machine

- Opened Oracle VirtualBox.
- Selected **New**.
- Named the virtual machine.
- Selected:
  - Type: Microsoft Windows
  - Version: Windows 11 (64-bit)

---

### Step 2 — Allocate Resources

Configured:

- RAM
- CPU cores

Ensured sufficient resources were allocated for Windows 11.

---

### Step 3 — Create Virtual Storage

Created a new virtual hard disk.

Selected:

- VDI (VirtualBox Disk Image)
- Dynamically Allocated
- Appropriate storage size

---

### Step 4 — Attach the Windows 11 ISO

Opened:

Settings → Storage

Attached the Windows 11 installation ISO as the virtual optical drive.

---

### Step 5 — Install Windows 11

Started the virtual machine.

Completed the Windows installation wizard by:

- Selecting language and keyboard layout
- Accepting license terms
- Selecting the virtual disk
- Installing Windows
- Completing the Out-of-Box Experience (OOBE)

---

### Step 6 — Complete Initial Setup

Configured:

- User account
- Password
- Windows settings

Logged into Windows successfully.

---

## Verification

Verified that:

- Windows booted successfully.
- Desktop loaded correctly.
- Device Manager showed no critical hardware issues.
- The VM was ready for future labs.

---

## Common Problems That May Occur

During Windows installation, you may encounter issues such as:

- Insufficient RAM allocated to the VM.
- Virtual hard disk not attached.
- Windows ISO not attached correctly.
- TPM or Secure Boot requirements (depending on VM configuration).
- Boot order incorrectly configured.

These issues can occur on both virtual machines and physical computers, although TPM and Secure Boot configuration may differ depending on the hardware.

---

## How I Would Explain This to a User

> "I installed a fresh copy of Windows by preparing the computer, creating the required storage, booting from the installation media, and completing the setup process. After installation, I verified that Windows started correctly and that the system was ready for use."

---

## What I Would Check on a Real PC

1. Verify the installation media is bootable.
2. Confirm the SSD or HDD is detected.
3. Check BIOS/UEFI boot order.
4. Ensure the system meets Windows 11 hardware requirements.
5. Verify TPM and Secure Boot if Windows 11 is being installed.
6. Confirm there is sufficient disk space.

---

## Lessons Learned

- Installing Windows follows a structured process regardless of whether it is installed on a virtual machine or a physical computer.
- Proper VM configuration is essential before starting the installation.
- Correct storage and memory allocation prevent many installation problems.
- Verifying the system after installation ensures it is ready for troubleshooting and administrative tasks.
