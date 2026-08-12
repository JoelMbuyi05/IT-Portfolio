# Day 01 — Tenant Foundations and DNS
Date: 08 August 2026
Study time: [how long you actually spent]
Source: Microsoft Learn + [any YouTube video you watched]

---

## What I Learned Today
[Write this in your own words after studying.
Not copy-pasted. Your own words.
Example below:]

The Microsoft 365 Developer Tenant is a free sandbox
environment that gives you a full enterprise Microsoft
setup — Entra ID, Intune, Exchange, Teams, SharePoint —
with 25 fake users. It's what I use to practice
everything MD-102 covers without needing a real company.

DNS records connect your domain to Microsoft 365 services.
Three main records to know:
- MX record: tells the internet where to deliver email
  for your domain
- TXT record: proves to Microsoft that you own the domain
- CNAME record: points services like Autodiscover to
  Microsoft's servers

---

## Key Concepts
[Bullet points — short, specific, your words]

- Tenant = your organisation's dedicated M365 environment
- Every tenant has a default domain: xyz.onmicrosoft.com
- Custom domain requires DNS verification via TXT record
- MX record must point to Microsoft for email to work
- Without correct DNS records → email fails, services broken

---

## Commands I Used
[Paste every command you ran today]

# Checked DNS records via PowerShell
nslookup -type=MX yourdomain.com
nslookup -type=TXT yourdomain.com

---

## What Confused Me
[Be honest — what didn't click immediately]

---

## How This Connects to the Job
When a user reports email not arriving, the first
thing I check is MX records — if they're wrong or
missing, no email gets delivered. I use nslookup
to verify records are correct without needing
access to the domain registrar.

---

## Exam Tips
- Know all three DNS record types and what each does
- MX = mail, TXT = verification, CNAME = service alias
- Understand that DNS changes take time to propagate
  (up to 48 hours — TTL dependent)

---

## Wrong Answers From Practice Questions
Q: [paste the question you got wrong]
Correct answer: [what it should be]
Why I got it wrong: [your honest reason]
What I now know: [the correct understanding]