# Lab-002 — BIOS and UEFI Basics

## Date

27 July 2026

## Goal

Understand the purpose of BIOS/UEFI, how it initializes hardware during startup, and what settings an IT Support technician would verify during troubleshooting.

## Environment

- Host OS: Windows 11
- Hypervisor: Oracle VirtualBox
- Guest OS: Windows 11
- VM Name: Win11-Lab1

---

# Attempt

## Objective

Attempt to access the VM firmware (BIOS/UEFI) during startup.

## Procedure

1. Powered on the virtual machine.
2. Attempted to enter the firmware setup using **F2** during startup.

## Explanation

Many virtual machines use different keys to access the firmware (such as **F2**, **Esc**, or **Delete**) depending on the hypervisor and firmware configuration. In VirtualBox, the firmware setup may also require different VM settings or a slower boot process.

---

# What is BIOS?

**BIOS (Basic Input/Output System)** is firmware that initializes hardware when a computer starts and begins the boot process by locating a bootable device.

Typical BIOS responsibilities include:

- Detecting installed RAM
- Detecting storage devices
- Detecting the CPU
- Checking connected hardware
- Starting the operating system

---

# What is UEFI?

**UEFI (Unified Extensible Firmware Interface)** is the modern replacement for BIOS.

Compared to legacy BIOS, UEFI provides:

- Faster startup
- Secure Boot support
- GPT disk support
- Better hardware compatibility
- Larger disk support (greater than 2 TB)

---

# What I Would Check in BIOS/UEFI on a Real PC

1. Verify the installed RAM is detected correctly.
2. Confirm the SSD or HDD is detected.
3. Check the boot order.
4. Verify the correct date and time.
5. Check CPU information.
6. Restore default settings if incorrect configuration is suspected.
7. Check whether Secure Boot is enabled or disabled when appropriate.

---

# Common Problems Found in BIOS/UEFI

- RAM not detected
- SSD/HDD not detected
- Incorrect boot order
- Disabled virtualization
- Incorrect system time
- Secure Boot configuration issues

---

## How I Would Explain This to a User

> "The BIOS or UEFI is the firmware that starts your computer before Windows loads. I'll check whether your hardware, such as the memory and storage drive, is being detected correctly and verify that the computer is configured to boot from the correct device."

---

## Lessons Learned

- BIOS/UEFI initializes hardware before Windows starts.
- Incorrect firmware settings can prevent Windows from booting.
- Verifying hardware detection and boot order is one of the first steps when troubleshooting startup issues.
- Modern systems typically use UEFI instead of the legacy BIOS.

## Screenshots

![alt text](image.png)