# Day 04 — Networking Fundamentals

**Date:** 8/15/2026
**Source:** Microsoft Learn — *Explore networking fundamentals*

---

## What I Learned Today

Today I reviewed networking fundamentals and connected the concepts to Microsoft 365 and IT support troubleshooting.

I learned how devices communicate using IP addresses and how the subnet mask determines which addresses are considered part of the local network.

I also practiced configuring a Windows VM with a static IP address and then restoring it to DHCP.

The main concepts I focused on were IP addressing, subnet masks, default gateways, DNS, DHCP and APIPA.

A private IP address is used inside a private network and is not directly routable across the public Internet.

The subnet mask determines the network and host portions of an IP address. For example, `255.255.255.0` is a `/24` network and provides 254 usable host addresses.

The default gateway is normally the router that a device uses to reach destinations outside its local network.

DNS translates human-readable names such as `google.com` into IP addresses.

DHCP automatically provides network configuration such as an IP address, subnet mask, gateway and DNS servers.

If a Windows device cannot obtain an address from DHCP, it can assign itself an APIPA address in the `169.254.x.x` range.

---

## Key Concepts

* **Private IP ranges:**

  * `10.0.0.0/8`
  * `172.16.0.0/12`
  * `192.168.0.0/16`

* **Subnet mask** = determines the network and host portions of an IP address.

* **/24** = `255.255.255.0`

* A `/24` has 256 total addresses and normally 254 usable host addresses.

* **Default gateway** = device/router used to reach networks outside the local subnet.

* **DNS** = resolves domain names to IP addresses.

* **DHCP** = automatically assigns network configuration to clients.

* **APIPA** = `169.254.x.x`; usually indicates that the client could not obtain an address from DHCP.

* **Static IP** = manually configured network information.

* **DHCP address** = automatically assigned network information.

---

## Commands I Used

```cmd
ipconfig /all
```

Used to view the current IP address, subnet mask, gateway, DNS servers and DHCP configuration.

```cmd
ping 8.8.8.8
```

Used to test connectivity to an Internet IP address without depending on DNS name resolution.

```cmd
ping google.com
```

Used to test connectivity while also requiring DNS name resolution.

```cmd
nslookup google.com
```

Used to query DNS and see how `google.com` resolves.

```cmd
tracert google.com
```

Used to view the route/hops taken toward the destination.

```cmd
ipconfig /release
```

Used to release the current DHCP configuration.

```cmd
ipconfig /renew
```

Used to request a new DHCP configuration.

---

## What I Practiced

I configured the Windows VM with a static IPv4 configuration:

```text
IP address:       192.168.1.50
Subnet mask:      255.255.255.0
Default gateway: 192.168.1.1
DNS:              8.8.8.8
Alternate DNS:    8.8.4.4
```

I then tested the configuration using `ipconfig`, `ping`, `nslookup` and `tracert`.

I changed the subnet mask from:

```text
255.255.255.0
```

to:

```text
255.255.0.0
```

and tested connectivity to the gateway to observe how changing the subnet mask affects the client's understanding of the local network.

Finally, I restored the adapter to DHCP and used `ipconfig /release` and `ipconfig /renew` to obtain network configuration automatically again.

---

## What Confused Me

At first I thought changing the subnet mask would immediately disconnect the computer from the network. I learned that this is not necessarily the case. The effect depends on the addresses involved and which destinations Windows now considers to be local.

This helped me understand that a network problem is not always simply "connected" or "disconnected." A device can still have connectivity while having an incorrect network configuration.

---

## How This Connects to the Job

If a user says they have no Internet connection, I can troubleshoot the problem systematically.

I can start with:

```cmd
ipconfig /all
```

Then check:

1. Does the computer have a valid IP?
2. Is it using an APIPA address?
3. Is the subnet mask correct?
4. Is a default gateway present?
5. Can I ping the gateway?
6. Can I reach an Internet IP such as `8.8.8.8`?
7. Can DNS resolve a domain?
8. Does `tracert` show where traffic stops?

This gives me a structured way to determine whether the problem is with the local configuration, gateway, Internet connection or DNS.

---

## Exam Tips

* `10.x.x.x` = private IP range.
* `172.16.x.x` through `172.31.x.x` = private range.
* `192.168.x.x` = private range.
* `/24` = `255.255.255.0`.
* `/24` = 254 usable host addresses.
* Default gateway provides the path to other networks.
* DNS resolves names to IP addresses.
* DHCP automatically provides IP configuration.
* `169.254.x.x` usually indicates a DHCP/address-assignment problem.
* `ping 8.8.8.8` tests IP connectivity without requiring DNS.
* `ping google.com` tests connectivity plus DNS resolution.
* `nslookup` specifically investigates DNS.
* `tracert` shows the path toward a destination.

---

## Defend Question — Answer Out Loud

**Question:** A user says their computer has no Internet. Walk me through your troubleshooting.

**Answer:**

First, I would check the physical or network connection and then run `ipconfig /all` to see whether the computer has a valid IP address, subnet mask, default gateway and DNS server. If I see a `169.254.x.x` address, I would suspect a DHCP problem. I would then ping the default gateway to test local network connectivity. If that works, I would ping `8.8.8.8` to test Internet connectivity without DNS. If that works but `ping google.com` fails, I would investigate DNS. I could then use `nslookup` to test DNS resolution and `tracert` to identify where traffic may be failing.

---

## Wrong Answers From Practice Questions

**Q:** [Paste the question you got wrong]

**Correct answer:** [Answer]

**Why I got it wrong:** [Your honest reason]

**What I now know:** [Correct understanding]
