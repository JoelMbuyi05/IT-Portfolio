# Tenant Foundations and DNS

**Date:** 12 August 2026
**Source:** Microsoft Learn

---

## What I Learned Today

I started a Microsoft 365 E5 trial so I can use a real Microsoft 365 environment to practice IT support tasks and prepare for the MD-102 exam.

A Microsoft 365 tenant is the organisation's own Microsoft cloud environment. It contains services such as Microsoft Entra ID, Microsoft 365 administration, Exchange Online, Teams, SharePoint and Intune.

The tenant has a default Microsoft domain ending in `onmicrosoft.com`. A custom domain can also be connected to Microsoft 365.

DNS is important because it tells computers and services where different parts of a domain should go.

The main DNS records I studied today were:

* **MX** — tells mail servers where email for a domain should be delivered.
* **TXT** — stores text information. Microsoft uses TXT records for things such as proving domain ownership and SPF.
* **CNAME** — creates an alias that points one hostname to another hostname. Microsoft 365 uses CNAME records for services such as Autodiscover and other service configurations.
* **SRV** — identifies the location of specific services and is also used by some Microsoft 365 services.

Microsoft 365 shows me the DNS records that need to be created when connecting a custom domain. The actual records have to be configured at the domain's DNS hosting provider/registrar unless the provider supports automatic Domain Connect configuration.

---

## Key Concepts

* **Tenant** = my organisation's dedicated Microsoft 365 cloud environment.
* **Default domain** = the `onmicrosoft.com` domain created with the tenant.
* **Custom domain** = a domain such as `company.com` that can be connected to Microsoft 365.
* **MX** = controls where email is delivered.
* **TXT** = can be used for domain verification and SPF information.
* **CNAME** = points one hostname to another hostname.
* **SRV** = provides service location information for supported services.
* **DNS hosting provider/registrar** = where the domain's DNS records are managed.
* DNS problems can cause Microsoft 365 services such as email or automatic configuration to fail.
* DNS changes can take time to appear because of DNS caching and TTL values.

---

## Commands I Used

```text
nslookup -type=MX outlook.com
nslookup -type=TXT outlook.com
nslookup -type=CNAME autodiscover.outlook.com
```

I used `nslookup` to query DNS records from Command Prompt and observe what information DNS returns.

---


## How This Connects to the Job

If a user reports that email is not arriving, I can investigate whether DNS is involved.

For a custom domain, I can check the MX record using `nslookup` to see where the domain's email is being directed.

For example:

```text
nslookup -type=MX company.com
```

If the MX record is missing or pointing to the wrong mail provider, email delivery can fail.

This gives me a practical troubleshooting method instead of simply assuming that the user's Outlook application is broken.

---

## Exam Tips

* **MX = mail delivery**
* **TXT = verification / text information / SPF**
* **CNAME = alias**
* **SRV = service location**
* Microsoft 365 can display the DNS records required when connecting a custom domain.
* DNS records are normally managed at the DNS hosting provider/registrar.
* DNS changes can take time to propagate because of caching and TTL.
