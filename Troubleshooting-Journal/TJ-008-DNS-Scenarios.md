# TJ-008 — DNS Resolution Failure

Date: 8/15/2026
Environment: Windows 11 Lab VM — Win11-Lab1

==================================================
SCENARIO
==================================================

A user reports:

"I can't access websites. Google isn't loading."

The user believes that the Internet connection is down.

My objective is to determine whether the problem is caused
by the computer's network configuration, local network,
Internet connectivity, or DNS.

==================================================
INITIAL SYMPTOM
==================================================

The user cannot access websites using domain names such as:

google.com

==================================================
STEP 1 — CHECK IP CONFIGURATION
==================================================

Command:

ipconfig /all

I checked:

- IPv4 address
- Subnet mask
- Default gateway
- DNS server

Result:

The computer had a valid IP address and a default gateway.

Conclusion:

The computer had a basic network configuration.

==================================================
STEP 2 — TEST THE DEFAULT GATEWAY
==================================================

Command:

ping <default-gateway>

Result:

The gateway responded successfully.

Conclusion:

The computer could communicate with the local network/router.

==================================================
STEP 3 — TEST INTERNET CONNECTIVITY WITHOUT DNS
==================================================

Command:

ping 8.8.8.8

Result:

The ping was successful.

Conclusion:

The computer had Internet connectivity by IP address.

This made a general Internet connectivity problem less
likely.

==================================================
STEP 4 — TEST CONNECTIVITY USING A HOSTNAME
==================================================

Command:

ping google.com

Result:

The hostname could not be resolved.

Conclusion:

DNS became the main suspect.

==================================================
STEP 5 — TEST DNS DIRECTLY
==================================================

Command:

nslookup google.com

Result:

DNS resolution failed/timed out.

Conclusion:

The DNS resolution process was failing.

==================================================
STEP 6 — CHECK DNS CONFIGURATION
==================================================

Command:

ipconfig /all

I discovered that the DNS server was incorrectly configured
as:

1.2.3.4

This was not a functioning DNS server for the lab.

==================================================
ROOT CAUSE
==================================================

The computer was using an incorrect DNS server.

The computer itself had:

- Valid IP address
- Working gateway
- Internet connectivity by IP

But it could not translate:

google.com
    ↓
IP address

because the configured DNS server was not functioning.

==================================================
FIX
==================================================

I restored the DNS configuration to automatic/DHCP.

I then cleared the local DNS cache:

ipconfig /flushdns

I renewed the network configuration:

ipconfig /renew

==================================================
VERIFICATION
==================================================

I tested DNS again:

nslookup google.com

Result:

The DNS query successfully returned an IP address.

I then tested:

ping google.com

Result:

The hostname successfully resolved and the destination
responded.

Finally, I tested web browsing and confirmed that websites
were accessible again.

==================================================
FINAL RESULTS
==================================================

| Test | Before Fix | After Fix |
|------|------------|-----------|
| ipconfig /all | Valid IP, incorrect DNS | Correct DNS |
| Ping gateway | Works | Works |
| ping 8.8.8.8 | Works | Works |
| nslookup google.com | Fails | Works |
| ping google.com | Fails | Works |
| Web browsing | Fails | Works |

==================================================
ROOT CAUSE
==================================================

Incorrect DNS server configuration.

The network connection itself was working. The failure
occurred specifically when the computer attempted to resolve
domain names.

==================================================
TROUBLESHOOTING LOGIC
==================================================

I isolated the problem step by step:

IP configuration
        ↓
Gateway
        ↓
Internet by IP
        ↓
DNS resolution
        ↓
Identify DNS failure
        ↓
Check DNS configuration
        ↓
Correct DNS
        ↓
Verify

==================================================
WHAT I LEARNED
==================================================

I learned not to automatically assume:

"Websites aren't loading = Internet is down."

A computer can have a functioning Internet connection while
DNS is broken.

The key comparison is:

ping 8.8.8.8
    → works

ping google.com
    → fails

When this happens, DNS should be one of the first things I
investigate.

==================================================
REAL IT SUPPORT CONNECTION
==================================================

This is a realistic Tier 1 support scenario.

If a user reports that websites are not loading, I can
determine whether the problem is:

- Local network connectivity
- Gateway/router
- Internet connection
- DNS configuration
- DNS server availability
- Firewall blocking DNS

Instead of guessing, I can isolate the failure one step at
a time.

==================================================
FINAL DIAGNOSIS
==================================================

Issue:
Websites could not be accessed by hostname.

Root Cause:
Incorrect DNS server configuration.

Fix:
Restored correct/automatic DNS configuration and refreshed
the network/DNS configuration.

Verification:
DNS resolution and web access were successfully restored.

Troubleshooting Skill Demonstrated:
Separating Internet connectivity problems from DNS resolution
problems using structured testing.