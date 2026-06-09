# 🌐 DNS — Domain Name System Learning Notes

> **Author:** Nicholas Ssemakula | BSc Cybersecurity & Digital Forensics — Nkumba University  
> **Topic:** DNS Fundamentals for Cybersecurity  
> **Source:** TryHackMe + Personal Study Notes  
> **Last Updated:** June 2026

---

## 📌 Table of Contents

1. [What is DNS?](#what-is-dns)
2. [DNS Records](#dns-records)
   - [A Record](#a-record)
   - [MX Record](#mx-record)
   - [TXT Record](#txt-record)
3. [How a DNS Request Works](#how-a-dns-request-works)
4. [Email Security via DNS (SPF, DKIM, DMARC)](#email-security-via-dns)
5. [Key Terms Glossary](#key-terms-glossary)
6. [Related VPN Protocols (PPP)](#related---ppp-vpn-technology)
7. [Resources](#resources)

---

## What is DNS?

**DNS (Domain Name System)** is often called the *phone book of the internet*. It translates human-readable domain names like `www.google.com` into IP addresses like `142.250.185.46` that computers use to communicate.

> Without DNS, you would have to memorize IP addresses to visit every website.

---

## DNS Records

DNS records are instructions stored in DNS servers that tell the internet how to handle requests for a domain.

---

### A Record

| Field | Value |
|---|---|
| **Type** | A |
| **Purpose** | Maps a domain name to an IPv4 address |
| **Example** | `example.com → 93.184.216.34` |

> The most fundamental DNS record — it answers: *"Where is this website?"*

---

### MX Record

**MX (Mail Exchanger)** record tells the internet **which server handles incoming email** for a domain.

```
example.com  MX  10  mail.example.com
example.com  MX  20  backup-mail.example.com
```

**Key Points:**
- Lower priority number = tried **first**
- Multiple MX records provide **redundancy** (backup servers)
- Points to a **hostname**, not an IP address directly

**Simple Analogy:**
> MX record = the **mailroom address** of a company. All incoming mail goes there, not the front door.

**Priority Logic:**
```
Try mail.example.com (priority 10) first
    ↓ if down
Try backup-mail.example.com (priority 20)
```

---

### TXT Record

**TXT (Text)** record stores plain text information in DNS — mainly used for **verification and email security**.

```
example.com  TXT  "v=spf1 include:gmail.com ~all"
example.com  TXT  "google-site-verification=abc123xyz"
```

**Main Uses:**

| Use Case | What it Does |
|---|---|
| **SPF** | Declares which servers can send email for your domain |
| **DKIM** | Stores a public key to verify email authenticity |
| **DMARC** | Sets policy for failed SPF/DKIM checks |
| **Domain Verification** | Proves you own the domain to Google, Microsoft, etc. |

**Simple Analogy:**
> TXT record = a **notice board** outside your domain. It holds important notes for servers and services that need to verify things about you.

---

## How a DNS Request Works

When you type `www.google.com` in your browser, here is what happens behind the scenes:

### Step-by-Step Journey

```
You type: www.google.com
          │
          ▼
┌─────────────────────┐
│   Browser Cache     │ ──── Hit? ✅ Done immediately
└─────────────────────┘
          │ Miss
          ▼
┌─────────────────────┐
│     OS Cache        │ ──── Hit? ✅ Done
└─────────────────────┘
          │ Miss
          ▼
┌──────────────────────────┐
│  Recursive DNS Resolver  │ ◄── Provided by ISP or 8.8.8.8 / 1.1.1.1
│  (The Librarian)         │ ──── Has local cache too
└──────────────────────────┘
          │ Not cached
          ▼
┌──────────────────────────┐
│   Root Name Server       │ ──── "Go ask the .com TLD server"
│   (Internet backbone)    │
└──────────────────────────┘
          │
          ▼
┌──────────────────────────┐
│   TLD Name Server        │ ──── "Go ask ns1.google.com"
│   (.com / .org / .ug)    │
└──────────────────────────┘
          │
          ▼
┌──────────────────────────┐
│ Authoritative Name Server│ ──── "IP = 142.250.185.46" ✅
│ (Google's own DNS)       │
└──────────────────────────┘
          │
          ▼
   Answer returns to Recursive Resolver
          │
          ▼
   Resolver caches + sends IP to your PC
          │
          ▼
   Browser connects to 142.250.185.46 🌐
```

---

### Key Players Explained

| Player | Role | Analogy |
|---|---|---|
| **Browser/OS Cache** | Checks saved answers first | Remembering a friend's number |
| **Recursive Resolver** | Does the leg work for you | A librarian who knows who to ask |
| **Root Name Server** | Knows where all TLD servers are | Knows which city to look in |
| **TLD Name Server** | Handles `.com`, `.org`, `.ug` etc. | Knows which street in the city |
| **Authoritative Name Server** | Has the exact, final answer | The actual house number |

---

### TTL — Time To Live

Every DNS record has a **TTL value (in seconds)** that controls how long the answer is cached before it must be looked up again.

```
TTL = 3600  →  Cache the answer for 1 hour
TTL = 86400 →  Cache for 24 hours
TTL = 300   →  Cache for 5 minutes (fast-changing records)
```

> Lower TTL = more DNS queries but faster propagation of changes  
> Higher TTL = fewer queries but slower updates

---

## Email Security via DNS

Three TXT records work together to protect email:

### How They Work Together

```
Incoming email claims to be from example.com
              │
              ▼
      ┌───────────────┐
      │  SPF Check    │ ──── Is this server allowed to send?
      └───────────────┘
              │
              ▼
      ┌───────────────┐
      │  DKIM Check   │ ──── Is the email's signature valid?
      └───────────────┘
              │
              ▼
      ┌───────────────┐
      │  DMARC Policy │ ──── What to do if checks fail?
      └───────────────┘
              │
        ┌─────┴─────┐
        ▼           ▼
   Accept ✅    Reject / Quarantine ❌
```

### SPF Record Example
```
v=spf1 include:gmail.com ~all
```
> *"Only Gmail servers may send email from @example.com"*

### DKIM Record Example
```
v=DKIM1; k=rsa; p=MIGfMA0GCSq...
```
> *"Here is our public key — use it to verify our emails are genuine"*

### DMARC Record Example
```
v=DMARC1; p=reject; rua=mailto:reports@example.com
```
> *"Reject emails that fail our checks, and send us a report"*

---

## Key Terms Glossary

| Term | Definition |
|---|---|
| **DNS** | Domain Name System — translates domain names to IP addresses |
| **DNS Query** | A question sent to a DNS server |
| **DNS Response** | The answer returned by a DNS server |
| **Recursive Resolver** | A server that does the full DNS lookup on your behalf |
| **Root Name Server** | Top-level DNS servers that know where all TLD servers are |
| **TLD** | Top-Level Domain (`.com`, `.org`, `.ug`, `.net`) |
| **Authoritative Name Server** | The final DNS server with definitive answers for a domain |
| **TTL** | Time To Live — how long a DNS answer is cached |
| **Cache** | Saved DNS answers to avoid repeating lookups |
| **MX Record** | Mail Exchanger — directs incoming email |
| **TXT Record** | Text record — used for verification and email security |
| **SPF** | Sender Policy Framework — authorises email senders |
| **DKIM** | DomainKeys Identified Mail — email signature verification |
| **DMARC** | Domain-based Message Authentication — email policy enforcement |

---

## Related — PPP VPN Technology

**PPP (Point-to-Point Protocol)** is a Layer 2 protocol that forms the foundation of many VPN technologies.

### PPP-Based VPN Protocols

| Protocol | Description |
|---|---|
| **PPTP** | Tunnels PPP frames inside GRE over IP — fast but outdated/insecure |
| **L2TP/IPSec** | PPP over UDP + IPSec encryption — more secure than PPTP |
| **PPPoE** | PPP over Ethernet — used by ISPs for broadband (DSL) connections |

### PPP Authentication Methods

| Method | Security Level |
|---|---|
| **PAP** | Weak — sends credentials in plaintext |
| **CHAP** | Stronger — uses challenge-response |
| **MS-CHAPv2** | Microsoft version — used in PPTP (has known vulnerabilities) |
| **EAP** | Modern — supports certificates and tokens |

> ⚠️ **PPTP is considered insecure today.** Modern VPNs use **WireGuard**, **OpenVPN**, or **IKEv2/IPSec** instead.

---

## Resources

| Resource | Link |
|---|---|
| TryHackMe DNS Room | [tryhackme.com](https://tryhackme.com) |
| Cloudflare DNS Learning | [cloudflare.com/learning/dns](https://www.cloudflare.com/learning/dns/) |
| RFC 1035 — DNS Specification | [rfc-editor.org](https://www.rfc-editor.org/rfc/rfc1035) |
| MXToolbox (DNS Lookup Tool) | [mxtoolbox.com](https://mxtoolbox.com) |

---

## 📝 Study Checklist

- [ ] Understand what DNS is and why it exists
- [ ] Know the difference between A, MX, TXT, CNAME, and NS records
- [ ] Be able to explain the full DNS resolution journey
- [ ] Understand TTL and caching
- [ ] Know how SPF, DKIM, and DMARC protect email
- [ ] Understand DNS attack types (spoofing, poisoning, amplification)
- [ ] Practice DNS lookups using `nslookup` or `dig` on Kali Linux

---

> 📂 *Part of my Cybersecurity & Digital Forensics learning journey at Nkumba University*  
> 🔗 *Connect: [LinkedIn](#) | [GitHub](#)*
