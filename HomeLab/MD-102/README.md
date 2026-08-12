# Lab 009 — Tenant Setup and DNS Configuration
Date: 08 August 2026
Duration: [actual time spent]
Day: 01 of 30-day MD-102 plan

---

## Goal
Set up Microsoft 365 Developer Tenant and explore
DNS record configuration for a custom domain.

---

## Environment
- Microsoft 365 Developer Tenant
- Browser: Edge or Chrome
- Admin center: admin.microsoft.com
- Entra admin: entra.microsoft.com

---

## Steps I Took
[Number every step. Write as you do it, not after.]

1. Went to developer.microsoft.com/microsoft-365/dev-program
2. Signed in with my Microsoft account
3. Clicked Set Up E5 Sandbox → Instant sandbox
4. Noted my tenant domain: [yourtenant].onmicrosoft.com
5. Logged into admin.microsoft.com with admin credentials
6. Navigated to Settings → Domains → viewed default domain
7. Clicked Add Domain → entered a fake domain for practice
8. Viewed the DNS records Microsoft requires:
   - TXT record for verification
   - MX record for email
   - CNAME records for services
9. Opened Command Prompt → ran:
   nslookup -type=MX outlook.com
   (used outlook.com as example since fake domain
   has no real DNS)
10. Explored all sections of admin.microsoft.com

---

## Commands Used
nslookup -type=MX outlook.com
nslookup -type=TXT outlook.com
nslookup -type=CNAME autodiscover.outlook.com

---

## What Broke
[Anything that didn't work as expected]

---

## How I Fixed It
[What you did to resolve it]

---

## Screenshots
[Drag screenshots into HomeLab/screenshots/ folder]
![Tenant admin center](./screenshots/lab009-admin-center.png)
![DNS records view](./screenshots/lab009-dns-records.png)

---

## Lessons Learned
DNS records are what make Microsoft 365 services
actually work for a custom domain. Without correct
MX records email routing breaks completely. I can
now explain to a user why their email stopped
working after a domain transfer — the MX record
likely didn't carry over correctly.

---

## Exam Connection
MD-102 expects you to understand what DNS records
are required for Microsoft 365 and why. MX, TXT,
and CNAME are the three to know cold.

---

## Real Job Connection
When a company switches domain registrars or moves
to Microsoft 365, DNS misconfiguration is the most
common cause of mail flow failures. This lab gives
me the vocabulary and process to diagnose it.