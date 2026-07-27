# TJ-004 — Windows System Health Checks

## Environment
- Host OS: Windows 11
- Hypervisor: Oracle VirtualBox
- VM: Win11-Lab1

## Symptom
No major system issue was reported. This exercise was performed as a preventative health check to verify Windows system integrity and identify any hidden errors.

## Initial Theory
If Windows system files, disk structures, or the component store were corrupted, the built-in diagnostic tools would detect and report the issues.

## Was the Theory Correct?
No.

All diagnostic checks completed successfully, indicating the operating system was healthy.

## Troubleshooting Steps

### 1. System File Checker
Executed:

```cmd
sfc /scannow
```

Result:

> Windows Resource Protection did not find any integrity violations.

---

### 2. Disk Check

Executed:

```cmd
chkdsk C: /f
```

Result:

No file system errors requiring repair were found.

---

### 3. Deployment Image Servicing and Management (DISM)

Executed:

```cmd
DISM /Online /Cleanup-Image /RestoreHealth
```

Result:

The Windows component store was healthy and no corruption was detected.

---

### 4. Event Viewer

Opened:

Event Viewer → Windows Logs

Reviewed recent system events and investigated Event ID **7023**.

## Root Cause

No operating system corruption was detected.

The Event Viewer contained service-related events that can occur during normal system operation and were not caused by damaged system files.

## Fix

No repair was required.

The system health checks confirmed that Windows was functioning correctly.

## Verification

- SFC completed successfully.
- CHKDSK completed successfully.
- DISM completed successfully.
- Windows continued operating normally.

## What I'd Check First Next Time

- Review Event Viewer for recurring critical or error events.
- Run SFC before assuming Windows is corrupted.
- Run DISM if SFC reports unrepairable files.
- Run CHKDSK when storage corruption is suspected.

## Real-World Connection

These are standard diagnostic tools used by IT Support professionals to verify Windows health before performing more advanced troubleshooting or recommending an operating system reinstall.
