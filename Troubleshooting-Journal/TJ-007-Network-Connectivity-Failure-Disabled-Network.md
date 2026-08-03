# TJ-005 — Network Connectivity Failure Due to Disabled Network Adapter


## Environment

Host OS: Windows 11
Hypervisor: Oracle VirtualBox
Guest OS: Windows 11
VM: Win11-Lab1
Network Adapter: Intel(R) PRO/1000 MT Desktop Adapter (Disabled)

## Symptom
The VM could not access the network after the Ethernet adapter was disabled.

## Observed behaviour:
ping 127.0.0.1 succeeded.
ping 8.8.8.8 failed.
ping google.com failed.
The adapter appeared as disabled in Network Connections.

## Initial Theory
The network adapter had been disabled, preventing Windows from communicating with the network.

## Was the Theory Correct?
Yes.
Re-enabling the adapter immediately restored network connectivity.

## Troubleshooting Steps
- Checked the network status.
- Opened Network Connections.
- Confirmed the Ethernet adapter was disabled.
- Enabled the adapter.
- Waited for Windows to reconnect.
- Retested network connectivity.

## Root Cause
The Ethernet adapter was disabled, preventing any network communication.

## Fix
Enabled the network adapter.

## Verification
Windows obtained a valid IP address.
ping 127.0.0.1 succeeded.
ping 8.8.8.8 succeeded.
ping google.com succeeded.

## What I'd Check First Next Time
Verify the adapter is enabled.
Check Device Manager for hardware issues.
Verify cable or virtual adapter status.
Confirm an IP address has been assigned.

## Real-World Connection
A disabled network adapter is a common support issue caused by user error, hardware maintenance, or driver problems. During troubleshooting, I would first verify the adapter's status before investigating more complex networking issues.

## Screnshots
![alt text](image-8.png)
![alt text](image-9.png)