# 🔍 Performing Reconnaissance — OSINT & DNS Investigation

> **SOC+ Portfolio Project | April 2026**
> A hands-on reconnaissance project demonstrating passive and active information gathering techniques used in ethical hacking and penetration testing engagements.

---

## 📋 Project Overview

| Field | Details |
|-------|---------|
| **Environment** | Kali Linux (fully updated — v2026.2.0) |
| **Target** | example.com (IANA test domain) |
| **Type** | Passive & Semi-Passive Reconnaissance |
| **Tools Used** | whois, nslookup, dig, Google Dorking, Netcraft, PeekYou, SearchSystems |

---

## 🎯 Objective

To demonstrate the ability to perform reconnaissance using industry-standard tools — gathering information about a target's domain ownership, DNS infrastructure, hosting configuration, and public exposure — without directly interacting with or alerting the target.

---

## 🛠️ Tools & Techniques

| Tool | Category | Purpose |
|------|----------|---------|
| `whois` | Domain Recon | Query domain registration, ownership, expiry |
| `nslookup` | DNS Recon | Query NS, MX, SOA records interactively |
| `dig` | DNS Recon | Detailed DNS queries against public DNS servers |
| Google Dorking | OSINT | Find exposed files and credentials via search operators |
| Netcraft | OSINT | Analyse website infrastructure and technologies |
| PeekYou | People OSINT | Search publicly available personal information |
| SearchSystems | People OSINT | Access public government records databases |

---

## 📁 Project Structure

```
soc-recon-portfolio/
├── README.md                          # This file
├── report/
│   └── Performing_Reconnaissance_SOC_Project.pdf   # Full report with screenshots
└── outputs/
    ├── target_info.txt                # ping output
    ├── target_whois.txt               # whois output
    └── target_dns.txt                 # dig output
```

---

## 🔎 Key Findings

### Domain Reconnaissance (whois)
- `example.com` registered under **IANA** since **1995**
- DNS managed by **Cloudflare** nameservers
- Three domain locks in place (Delete, Transfer, Update Prohibited)
- **DNSSEC enabled** — domain is security hardened
- Domain expires **August 2026**

### DNS Reconnaissance (nslookup & dig)
- Domain resolves to **two IP addresses** (`172.66.147.243` and `104.20.23.154`) — confirming **load balancing**
- **No MX records** configured — domain does not send/receive email
- SOA record confirms **Cloudflare** manages the DNS zone
- Queries verified against Google public DNS (`8.8.8.8`)

### Google Dorking
- `site:example.com filetype:txt robots` — **No results** (no exposed directory structure)
- `intitle:password site:example.com` — **No results** (no exposed login pages)
- `filetype:cfg "enable password 7"` — **Results found** on third-party sites, demonstrating real-world exposure of Cisco device credentials

### Netcraft OSINT
- Site first seen: **December 1995**
- Hosted by **Cloudflare, Inc.** (United States)
- **SPF policy:** `-all` (reject all unauthorised senders)
- **DMARC policy:** `p=reject` (strict enforcement)
- **No web trackers** identified
- Technologies: Cloudflare CDN, Gzip compression, HTML5

### People OSINT
- PeekYou search attempted but tool was unresponsive
- SearchSystems confirmed access to **390+ record types** across 50 US states via government databases
- BeenVerified encountered but requires paid registration — not used

---

## 💡 Key Takeaways

1. **Significant information is publicly available** before any direct interaction with a target
2. **Cloudflare provides strong protection** — masking origin servers and enforcing strict email policies
3. **Google Dorking is a powerful passive technique** — capable of finding real exposed credentials on misconfigured systems
4. **Load balancing was detected** through multiple DNS queries returning different IPs
5. **example.com is well secured** — no exposed files, no email servers, DNSSEC enabled, strict DMARC/SPF

---

## ⚖️ Ethical Statement

All reconnaissance in this project was performed on `example.com`, a domain maintained by IANA specifically for documentation and testing purposes. No unauthorised systems were accessed at any point. All techniques were performed in a controlled lab environment using Kali Linux.

---

## 📚 Skills Demonstrated

- ✅ Linux command line (Kali Linux)
- ✅ DNS record analysis (A, NS, MX, SOA records)
- ✅ OSINT methodology
- ✅ Google Dorking techniques
- ✅ Domain and infrastructure reconnaissance
- ✅ Professional documentation and reporting
- ✅ Ethical hacking principles

---

*Part of an ongoing SOC+ cybersecurity upskilling portfolio.*
