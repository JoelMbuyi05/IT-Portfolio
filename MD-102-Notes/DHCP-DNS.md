# Day 05 — DNS Fundamentals

**Date:** 8/15/2026
**Source:** Microsoft Learn — *Explore DNS*

---

## What I Learned Today

Today I focused specifically on DNS and how Windows uses DNS to translate domain names into IP addresses.

DNS allows users and applications to use names such as `google.com` instead of having to remember an IP address.

I learned that DNS uses different **zones and record types** to store information about domains and services.

I also learned the basic DNS resolution process. When a client needs to access a domain name, it asks its configured DNS server to resolve the name. The DNS server either already knows the answer from its cache or queries other DNS servers until it can return an answer.

I practiced querying different DNS servers directly using `nslookup` and compared the results from Google's DNS server (`8.8.8.8`) and Cloudflare's DNS server (`1.1.1.1`).

I also deliberately broke DNS in several different ways. This helped me understand that a computer can still have an IP address and network connectivity while DNS is completely unavailable.

---

## Key Concepts

### DNS

**DNS = Domain Name System**

It translates names such as:

```text
google.com
```

into IP addresses.

---

### DNS Zone

A DNS zone is an administrative portion of the DNS namespace containing DNS records for a domain or part of a domain.

Examples include:

* Forward lookup zone → name to IP
* Reverse lookup zone → IP to name

---

### Important DNS Record Types

* **A** = hostname → IPv4 address
* **AAAA** = hostname → IPv6 address
* **CNAME** = alias → another hostname
* **MX** = specifies mail servers for a domain
* **TXT** = stores text information, commonly used for verification and email security
* **NS** = identifies authoritative name servers

---

### DNS Resolution

A simplified process is:

```text
User enters google.com
        ↓
Computer checks local DNS cache
        ↓
Computer queries configured DNS server
        ↓
DNS server finds/resolves the address
        ↓
IP address returned
        ↓
Computer connects to the destination
```

---

### Internal vs External DNS

**Internal DNS** is used inside an organisation's network and can resolve internal resources.

For example:

```text
fileserver.company.local
```

**External DNS** resolves public Internet domains.

For example:

```text
google.com
microsoft.com
```

---

## Commands I Used

### View the local DNS cache

```cmd
ipconfig /displaydns
```

This displays DNS records currently cached by Windows.

---

### Clear the DNS cache

```cmd
ipconfig /flushdns
```

This removes cached DNS entries so new queries have to be resolved again.

---

### Query the default DNS server

```cmd
nslookup google.com
```

This asks the computer's configured DNS server to resolve `google.com`.

---

### Query Google's DNS server

```cmd
nslookup google.com 8.8.8.8
```

This specifically asks Google's public DNS server.

---

### Query Cloudflare's DNS server

```cmd
nslookup google.com 1.1.1.1
```

This specifically asks Cloudflare's public DNS server.

---

## What I Learned From Comparing DNS Servers

I learned that I can query different DNS servers directly rather than relying only on the DNS server configured on my computer.

The returned IP addresses may differ because DNS providers can use different infrastructure, caching and load-balancing responses.

The important point is that the DNS servers can still successfully resolve the same domain even if the exact returned IP address differs.

---

## What Confused Me

At first I thought DNS was simply a database containing one IP address for every website. I now understand that DNS is a distributed system with multiple servers, zones, records, caching and different types of DNS queries.

I also learned that DNS problems are different from general network problems. A computer can successfully reach an IP address while being unable to resolve a domain name.

---

## How This Connects to the Job

DNS problems are extremely common in IT support.

For example, if:

```cmd
ping 8.8.8.8
```

works but:

```cmd
ping google.com
```

fails, I would investigate DNS rather than immediately assuming the Internet connection is down.

I can use:

```cmd
nslookup google.com
```

to determine whether DNS resolution is working.

I can also use:

```cmd
ipconfig /displaydns
ipconfig /flushdns
```

to inspect and clear the local DNS cache.

---

## Exam Tips

* DNS translates names into IP addresses.
* **A** = IPv4 address.
* **AAAA** = IPv6 address.
* **CNAME** = alias.
* **MX** = mail server.
* **TXT** = text/verification information.
* **NS** = name server.
* `ipconfig /displaydns` = view local DNS cache.
* `ipconfig /flushdns` = clear local DNS cache.
* `nslookup` = test DNS resolution.
* `8.8.8.8` = Google Public DNS.
* `1.1.1.1` = Cloudflare Public DNS.
* DNS failure does not necessarily mean Internet connectivity has failed.
* Internal DNS can resolve internal organisational resources.
* External DNS resolves public Internet resources.

---

## Defend Question — Answer Out Loud

"A user can access websites by IP address but not by name. What would you check?"

"I'd suspect DNS. I'd check the configured DNS server and use nslookup to test name resolution. I'd also check the local DNS cache and flush it if necessary."

---

## Wrong Answers From Practice Questions

1. What is the difference between DHCP and DNS?

Answer: DHCP provides network configuration; DNS resolves names to IP addresses.

2. What does ipconfig /displaydns do?

Answer: Shows the computer's local DNS cache.

3. What does ipconfig /flushdns do?

Answer: Clears the local DNS cache.

4. What does nslookup do?

Answer: Tests DNS name resolution.

5. What is an A record?

Answer: Maps a hostname to an IPv4 address.

6. What is a CNAME record?

Answer: Creates an alias for another hostname.

7. What is an MX record?

Answer: Identifies the mail servers responsible for a domain.

8. What is the difference between internal and external DNS?

Answer: Internal DNS resolves organizational resources; external DNS resolves public resources.

9. A user can ping 8.8.8.8 but can't access google.com. What do you suspect?

Answer: A DNS resolution problem.

10. What port does DNS commonly use?

Answer: UDP 53, with TCP 53 also used in some cases.
