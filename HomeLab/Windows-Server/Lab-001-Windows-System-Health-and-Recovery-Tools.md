# Lab-001 — Windows System Health and Recovery Tools

## Date

27 July 2026

## Goal

Learn how to verify the health of a Windows installation using built-in recovery and diagnostic tools.

## Environment

- Host OS: Windows 11
- Hypervisor: Oracle VirtualBox
- Guest OS: Windows 11
- VM Name: Win11-Lab1

---

# Test 1 — System File Checker (SFC)

## Objective

Verify the integrity of protected Windows system files.

## Command

```cmd
sfc /scannow
```

## Observations

The scan completed successfully.

Result:

> Windows Resource Protection did not find any integrity violations.

### What SFC Does

- Scans protected Windows system files.
- Detects missing or corrupted files.
- Automatically repairs files when possible.

---

# Test 2 — Check Disk (CHKDSK)

## Objective

Check the file system for errors.

## Command

```cmd
chkdsk C: /f
```

## Observations

The command completed successfully and no disk errors requiring repair were reported.

### What CHKDSK Does

- Checks the file system for corruption.
- Repairs logical disk errors.
- Identifies bad sectors when additional scan options are used.

---

# Test 3 — DISM

## Objective

Verify and repair the Windows Component Store.

## Command

```cmd
DISM /Online /Cleanup-Image /RestoreHealth
```

## Observations

The operation completed successfully.

No corruption was detected within the Windows image.

### What DISM Does

- Checks the Windows image for corruption.
- Repairs the Windows Component Store.
- Provides healthy files that SFC can use if repairs are needed.

---

# Test 4 — Event Viewer

## Objective

Review Windows system logs for warnings and errors.

## Procedure

1. Opened Event Viewer.
2. Navigated to **Windows Logs**.
3. Reviewed recent system events.
4. Investigated **Event ID 7023**.

## Observations

Event Viewer displayed historical system events, including Event ID 7023.

No evidence suggested that the event was caused by corrupted Windows system files.

---

## How I Would Explain This to a User

> "I checked the health of your Windows installation by scanning the system files, checking the disk for file system errors, verifying the Windows recovery image, and reviewing the system logs. All checks completed successfully, indicating that Windows itself is healthy."

---

## What I Would Check on a Real PC

1. Run `sfc /scannow`.
2. Run `DISM /Online /Cleanup-Image /RestoreHealth`.
3. Run `chkdsk` if storage problems are suspected.
4. Review Event Viewer for recurring critical or error events.
5. Verify SMART disk health using the manufacturer's diagnostic tools if hardware failure is suspected.

---

## Lessons Learned

- **SFC** verifies the integrity of protected Windows system files.
- **CHKDSK** checks the file system for logical errors.
- **DISM** repairs the Windows Component Store.
- **Event Viewer** provides historical logs that help diagnose system and application issues.
- Running these tools is a standard first step before considering Windows reinstallation or hardware replacement.
