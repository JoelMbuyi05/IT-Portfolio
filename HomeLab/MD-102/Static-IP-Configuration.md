# Lab 012 — Static IP Configuration and Network Troubleshooting

**Date:** 8/15/2026
**Day:** 04 of 30-day MD-102 plan

---

## Goal

Practice configuring IPv4 network settings manually, testing connectivity and DNS, deliberately changing a subnet mask, and restoring the computer to DHCP.

---

## Environment

* Windows 10 Lab VM
* VirtualBox
* Windows Command Prompt
* Network adapter
* IPv4 configuration

---

## Task 1 — Configure Static IP

### Steps I Took

1. Opened the Windows network settings.

2. Opened the network adapter properties.

3. Opened **Internet Protocol Version 4 (TCP/IPv4)** properties.

4. Changed the adapter from automatic configuration to manual configuration.

5. Configured the static IPv4 settings:

```text
IP address:       192.168.1.50
Subnet mask:      255.255.255.0
Default gateway: 192.168.1.1
Preferred DNS:    8.8.8.8
Alternate DNS:    8.8.4.4
```

6. Applied the configuration.

---

## Task 2 — Verify Network Configuration

I opened Command Prompt and ran:

```cmd
ipconfig /all
```

I checked:

* IPv4 address
* Subnet mask
* Default gateway
* DNS servers
* DHCP status

I documented the output and confirmed that the static configuration was applied.

---

## Task 3 — Test Connectivity

I ran:

```cmd
ping 8.8.8.8
```

### Result

[Record actual result.]

---

I then ran:

```cmd
ping google.com
```

### Result

[Record actual result.]

---

I then ran:

```cmd
nslookup google.com
```

### Result

[Record actual result.]

---

Finally:

```cmd
tracert google.com
```

### Result

[Record actual result.]

---

## Task 4 — Change the Subnet Mask

I deliberately changed the subnet mask from:

```text
255.255.255.0
```

to:

```text
255.255.0.0
```

I then tested the gateway.

```cmd
ping 192.168.1.1
```

### Result

[Record actual result.]

### What Changed?

Changing the subnet mask changed how Windows interpreted the local network.

The original:

```text
255.255.255.0
```

is `/24`.

The changed:

```text
255.255.0.0
```

is `/16`.

The `/16` configuration considers a much larger range of addresses to belong to the local network.

This demonstrated that an incorrect subnet mask can affect routing decisions even when the IP address itself has not changed.

---

## Task 5 — Restore DHCP

I returned to the IPv4 properties.

I selected:

**Obtain an IP address automatically**

and:

**Obtain DNS server address automatically**

I then ran:

```cmd
ipconfig /release
```

followed by:

```cmd
ipconfig /renew
```

Finally:

```cmd
ipconfig /all
```

I verified that the VM received its network configuration automatically from DHCP.

---

## Commands Used

```cmd
ipconfig /all
ping 8.8.8.8
ping google.com
nslookup google.com
tracert google.com
ipconfig /release
ipconfig /renew
```

---

## Troubleshooting Journal

### Test 1 — Static Configuration

**Expected:**
The VM should use the manually configured IP address, subnet mask, gateway and DNS servers.

**Actual:**
[Record actual result.]

**Conclusion:**
[Record conclusion.]

---

### Test 2 — Internet by IP

**Command:**

```cmd
ping 8.8.8.8
```

**Expected:**
Successful replies if Internet connectivity is working.

**Actual:**
[Record result.]

**Conclusion:**
This test checks IP connectivity without requiring DNS.

---

### Test 3 — Internet by Name

**Command:**

```cmd
ping google.com
```

**Expected:**
Successful resolution and connectivity.

**Actual:**
[Record result.]

**Conclusion:**
If `8.8.8.8` works but `google.com` fails, DNS becomes a strong suspect.

---

### Test 4 — DNS

**Command:**

```cmd
nslookup google.com
```

**Expected:**
DNS should return an IP address for `google.com`.

**Actual:**
[Record result.]

**Conclusion:**
[Record conclusion.]

---

### Test 5 — Route

**Command:**

```cmd
tracert google.com
```

**Expected:**
The command should display the network hops toward the destination.

**Actual:**
[Record result.]

**Conclusion:**
`tracert` can help identify where traffic appears to stop or become unreachable.

---

### Test 6 — Incorrect Subnet Mask

**Change:**

```text
255.255.255.0
↓
255.255.0.0
```

**Expected:**
The computer's interpretation of the local network should change.

**Actual:**
[Record whether the gateway ping worked.]

**Conclusion:**
The result showed that changing the subnet mask does not necessarily cause an immediate total loss of connectivity. Its effect depends on the network topology and addresses involved.

---

### Test 7 — DHCP Restoration

**Expected:**
The VM should receive an IP configuration automatically.

**Actual:**
[Record the new IP address.]

**Conclusion:**
DHCP successfully restored automatic network configuration.

---

## What Broke

[Document anything that actually failed.]

If everything worked:

**Nothing permanently broke. The subnet mask change was an intentional configuration error used to observe how the network behaves when the client's network definition is changed.**

---

## How I Fixed It

I restored the correct network configuration and then returned the adapter to DHCP.

I used:

```cmd
ipconfig /release
ipconfig /renew
```

to request a fresh configuration from the DHCP server.

---

## Screenshots

Save screenshots showing:

* Original `ipconfig /all`
* Static IPv4 configuration
* Static `ipconfig /all`
* `ping 8.8.8.8`
* `ping google.com`
* `nslookup google.com`
* `tracert google.com`
* Incorrect subnet mask
* Gateway ping after changing the subnet
* DHCP configuration
* Final `ipconfig /all`

Screenshot folder:

```text
HomeLab/screenshots/Day-04/
```

---

## Lessons Learned

I learned that IP configuration is made up of several components that work together.

The IP address identifies the device, the subnet mask determines which addresses are considered local, the default gateway provides a route to other networks, and DNS resolves names into IP addresses.

I also learned why troubleshooting should test each layer separately.

For example:

```text
Can I reach the gateway?
        ↓
Can I reach an Internet IP?
        ↓
Can DNS resolve a name?
        ↓
Can I reach the destination by name?
```

This gives me a much better troubleshooting process than simply saying "the Internet is down."

---

## Exam Connection

This lab reinforces important networking concepts used in Microsoft 365 and device administration.

I practiced:

* IPv4 addressing
* Private IP ranges
* Subnet masks
* CIDR `/24` notation
* Default gateways
* DNS
* DHCP
* APIPA
* Static IP configuration
* Network troubleshooting
* `ipconfig`
* `ping`
* `nslookup`
* `tracert`

These concepts are important because managed Windows devices and Microsoft 365 environments still depend on correct underlying network connectivity.

---

## Real Job Connection

A user might report:

> "My computer has no Internet."

Instead of immediately restarting the PC, I can systematically determine where connectivity stops.

For example:

```text
ipconfig /all
        ↓
Check IP configuration
        ↓
ping gateway
        ↓
Check local network
        ↓
ping 8.8.8.8
        ↓
Check Internet connectivity
        ↓
ping google.com
        ↓
Check DNS + connectivity
        ↓
nslookup
        ↓
Investigate DNS
```

This gives me a repeatable Tier 1 troubleshooting process that I can use before escalating the issue.
