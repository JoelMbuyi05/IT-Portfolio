# Lab 013 — DNS Break Fix Advanced

Date: 8/15/2026
Day: 05 of 30-day MD-102 plan

==================================================
GOAL
==================================================

Practice DNS diagnostics, compare different DNS servers,
deliberately break DNS in different ways, troubleshoot the
failures, and restore DNS functionality.

==================================================
ENVIRONMENT
==================================================

- Windows 10 Lab VM
- Win10-Lab1
- Windows Command Prompt
- Windows Defender Firewall
- DNS
- Google Public DNS
- Cloudflare Public DNS

==================================================
TASK 1 — DNS DIAGNOSTIC SEQUENCE
==================================================

1. Opened Command Prompt.

2. Checked the local DNS cache:

ipconfig /displaydns

Purpose:
To view DNS records currently cached by Windows.

Result:
[Record relevant output.]

3. Cleared the DNS cache:

ipconfig /flushdns

Result:
The DNS cache was successfully cleared.

4. Queried the computer's configured DNS server:

nslookup google.com

Result:
[Record DNS server and returned IP address.]

5. Queried Google's DNS server directly:

nslookup google.com 8.8.8.8

Result:
[Record result.]

6. Queried Cloudflare's DNS server directly:

nslookup google.com 1.1.1.1

Result:
[Record result.]

==================================================
DNS SERVER COMPARISON
==================================================

| Test | DNS Server | Result |
|------|------------|--------|
| nslookup google.com | Default DNS | [result] |
| nslookup google.com 8.8.8.8 | Google DNS | [result] |
| nslookup google.com 1.1.1.1 | Cloudflare DNS | [result] |

Observation:

The different DNS servers were able to resolve google.com.
The exact IP addresses returned may differ because DNS
providers can use different infrastructure, caching and
load-balancing.

The important point was that all functioning DNS servers
were able to resolve the domain.

==================================================
TASK 2 — BREAK DNS #1
==================================================

Deliberate fault:

Changed the DNS server to:

1.2.3.4

This was intentionally configured as a non-working DNS
server for the lab.

Tested:

ping google.com

and:

nslookup google.com

Expected result:

DNS resolution should fail because the configured DNS
server is not providing a valid response.

Actual result:

[Record actual result.]

Fix:

1. Restored DNS configuration to automatic/DHCP.
2. Cleared the DNS cache:

ipconfig /flushdns

3. Renewed the network configuration:

ipconfig /renew

4. Tested DNS again:

nslookup google.com

5. Tested:

ping google.com

Result:

[Record result.]

Lesson:

A computer can have a valid IP address and still be unable
to access websites by name if its DNS configuration is
incorrect.

==================================================
TASK 3 — BREAK DNS #2
==================================================

Deliberate fault:

Changed the DNS server to:

192.168.1.254

This address was intentionally selected because it was not
a functioning DNS server on the lab network.

Tested:

ping google.com

and:

nslookup google.com

Expected result:

DNS resolution should fail or time out because the
configured DNS server is unavailable.

Actual result:

[Record exact error/message.]

Fix:

1. Restored DNS configuration to automatic/DHCP.
2. Cleared the DNS cache:

ipconfig /flushdns

3. Renewed the configuration:

ipconfig /renew

4. Tested:

nslookup google.com

Result:

[Record result.]

Lesson:

An incorrect or unavailable DNS server can prevent name
resolution even when the computer has a valid IP address.

==================================================
TASK 4 — BREAK DNS #3 — WINDOWS FIREWALL
==================================================

Deliberate fault:

1. Opened Windows Defender Firewall with Advanced Security:

wf.msc

2. Navigated to:

Outbound Rules
→ New Rule
→ Port

3. Selected UDP.

4. Specified port:

53

5. Selected:

Block the connection

6. Applied the rule.

Tested:

nslookup google.com

and attempted to browse to a website.

Expected result:

DNS queries should fail because DNS traffic on UDP port 53
is being blocked.

Actual result:

[Record actual result.]

Fix:

1. Opened wf.msc.
2. Located the DNS blocking rule.
3. Deleted the rule.
4. Tested DNS again:

nslookup google.com

5. Tested web browsing again.

Result:

[Record result.]

Lesson:

DNS can fail because of a firewall rule even when the
computer has a valid IP address and Internet connectivity.

==================================================
COMMANDS USED
==================================================

ipconfig /displaydns

ipconfig /flushdns

nslookup google.com

nslookup google.com 8.8.8.8

nslookup google.com 1.1.1.1

ping google.com

ipconfig /renew

==================================================
WHAT BROKE
==================================================

Three intentional DNS failures were created:

1. Invalid DNS server: 1.2.3.4
2. Unavailable local DNS server: 192.168.1.254
3. Windows Firewall blocking UDP port 53

Each failure demonstrated a different possible cause of
DNS-related connectivity problems.

==================================================
HOW I FIXED IT
==================================================

Break 1:
Restored DNS to automatic/DHCP.

Break 2:
Restored DNS to automatic/DHCP.

Break 3:
Removed the Windows Firewall rule blocking UDP port 53.

After each fix, DNS resolution was tested again to verify
that the problem had been resolved.

==================================================
SCREENSHOTS
==================================================

Save screenshots in:

HomeLab/screenshots/Day-05/

Recommended screenshots:

1. ipconfig /displaydns
2. ipconfig /flushdns
3. nslookup google.com
4. nslookup google.com 8.8.8.8
5. nslookup google.com 1.1.1.1
6. DNS set to 1.2.3.4
7. Failed DNS test
8. DNS set to 192.168.1.254
9. Failed DNS test
10. Windows Firewall UDP 53 blocking rule
11. Failed DNS/browsing test
12. Deleted firewall rule
13. Successful DNS test after restoration

==================================================
LESSONS LEARNED
==================================================

I learned that DNS problems can have different causes.

A DNS server can be incorrectly configured, unavailable,
or blocked by a firewall.

The troubleshooting process is:

DNS configuration
        ↓
DNS server availability
        ↓
DNS resolution
        ↓
Firewall/network blocking DNS

I also learned that nslookup is useful because it allows
me to test DNS resolution directly instead of relying only
on a web browser.

==================================================
EXAM CONNECTION
==================================================

This lab reinforces:

- DNS zones
- DNS record types
- DNS resolution
- DNS caching
- Internal vs external DNS
- DNS troubleshooting
- DNS server configuration
- UDP port 53
- Windows Firewall
- nslookup
- ipconfig /displaydns
- ipconfig /flushdns

==================================================
REAL JOB CONNECTION
==================================================

If a user reports:

"My Internet isn't working."

I should determine whether the problem is actually Internet
connectivity or DNS.

For example:

ping 8.8.8.8
        ↓
Works
        ↓
ping google.com
        ↓
Fails
        ↓
Likely DNS problem

I can then use:

nslookup google.com

to investigate the DNS configuration and DNS server.

This gives me a structured troubleshooting process instead
of treating every Internet problem as the same issue.