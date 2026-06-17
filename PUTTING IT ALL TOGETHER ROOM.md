# 🧩 Putting It All Together — Web & Networking Fundamentals

**Author:** Nicholas Kiyimba | BSc Cybersecurity & Digital Forensics — Nkumba University
**Topic:** Complete Web & Networking Fundamentals Summary
**Source:** TryHackMe + Personal Study Notes
**Last Updated:** June 2026

---

## Table of Contents

1. [DNS — Domain Name System](#1-dns--domain-name-system)
2. [URLs — Uniform Resource Locators](#2-urls--uniform-resource-locators)
3. [HTTP Requests & Responses](#3-http-requests--responses)
4. [How Websites Work](#4-how-websites-work)
5. [Load Balancers](#5-load-balancers)
6. [CDN — Content Delivery Network](#6-cdn--content-delivery-network)
7. [Databases](#7-databases)
8. [WAF — Web Application Firewall](#8-waf--web-application-firewall)
9. [The Complete Picture](#9-the-complete-picture)
10. [Study Checklist](#10-study-checklist)

---

## 1. DNS — Domain Name System

DNS translates human-readable domain names into IP addresses computers can use.

**How a DNS request travels:**

```
Your Browser → Recursive Resolver → Root Server → TLD Server → Authoritative Server → IP returned
```

**Key DNS Records:**

| Record | Purpose |
|---|---|
| **A** | Maps domain to IPv4 address |
| **MX** | Directs incoming email to the right server |
| **TXT** | Stores verification info and email security (SPF, DKIM, DMARC) |
| **CNAME** | Alias — points one domain to another |

**TTL (Time To Live)** — controls how long a DNS answer is cached in seconds before it must be looked up again.

---

## 2. URLs — Uniform Resource Locators

A URL is the full address used to locate a specific resource on the internet.

```
https://www.tryhackme.com:443/room/dns?search=dns&page=2#results
  │        │        │      │     │            │             │
Protocol Subdomain Domain Port  Path        Query        Fragment
```

| Part | Purpose |
|---|---|
| **Protocol** | How to communicate (`http`, `https`, `ftp`) |
| **Subdomain** | Section of the site (`www`, `mail`, `api`) |
| **Domain** | The main registered address |
| **Port** | Which door to connect through (80=HTTP, 443=HTTPS) |
| **Path** | Which page or resource |
| **Query** | Extra parameters sent to the server |
| **Fragment** | Jump to a section within the page (browser only) |

> HTTPS = encrypted. HTTP = plaintext. Always look for the padlock.

---

## 3. HTTP Requests & Responses

HTTP is the language browsers and servers use to communicate.

**A basic request:**
```
GET /index.html HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0
Cookie: session=abc123
```

**HTTP Methods:**

| Method | Action |
|---|---|
| **GET** | Fetch data |
| **POST** | Send data |
| **PUT** | Update data |
| **DELETE** | Remove data |

**Key Status Codes:**

| Code | Meaning |
|---|---|
| **200** | OK — success |
| **301** | Moved Permanently |
| **401** | Unauthorised |
| **403** | Forbidden |
| **404** | Not Found |
| **500** | Internal Server Error |

**GET vs POST:**

| | GET | POST |
|---|---|---|
| Data location | URL (visible) | Request body (hidden) |
| Use for | Fetching pages | Login forms, sensitive data |

**Cookies** keep you logged in across requests. Key security flags:
- `HttpOnly` — blocks JavaScript from reading the cookie
- `Secure` — only sent over HTTPS
- `SameSite` — protects against CSRF attacks

---

## 4. How Websites Work

Every website is built from three layers:

| Layer | Technology | Role |
|---|---|---|
| Structure | HTML | Content and skeleton |
| Design | CSS | Colours, fonts, layout |
| Behaviour | JavaScript | Interactivity and logic |

**Static websites** — same files sent to everyone. No database needed.
**Dynamic websites** — pages built on the fly from a database per user.

**The Full Stack:**
```
┌─────────────────────────────────┐
│  FRONTEND — HTML + CSS + JS     │  ← Runs in your browser
├─────────────────────────────────┤
│  BACKEND — PHP / Python / Node  │  ← Business logic
├─────────────────────────────────┤
│  DATABASE — MySQL / MongoDB     │  ← Stores all data
└─────────────────────────────────┘
```

---

## 5. Load Balancers

When a website gets millions of visitors, one server cannot handle it all. A **load balancer** sits in front of multiple servers and **distributes incoming traffic** across them.

```
                  ┌─────────────┐
                  │             │──► Server 1
User Request ───► │ Load        │
                  │ Balancer    │──► Server 2
                  │             │
                  └─────────────┘──► Server 3
```

**What load balancers do:**

| Function | Description |
|---|---|
| **Traffic distribution** | Spreads requests so no single server is overwhelmed |
| **Health checks** | Regularly pings servers — if one goes down, traffic is rerouted |
| **Failover** | Automatically removes failed servers from the rotation |
| **Session persistence** | Ensures the same user always hits the same server if needed |

**Load balancing methods:**

| Method | How it works |
|---|---|
| **Round Robin** | Sends each request to the next server in turn |
| **Least Connections** | Sends to whichever server has fewest active connections |
| **IP Hash** | Same user IP always goes to the same server |

> Load balancers improve **availability**, **reliability**, and **scalability** of websites.

---

## 6. CDN — Content Delivery Network

A **CDN** is a global network of servers that stores **cached copies** of a website's static files (images, CSS, JS, videos) closer to the user.

```
Without CDN:
User in Kampala ──────────────────────► Server in USA (high latency)

With CDN:
User in Kampala ──► CDN Node in Nairobi ──► Content delivered fast ✅
```

**What CDNs do:**

| Function | Description |
|---|---|
| **Caching** | Stores static files at edge locations globally |
| **Speed** | Delivers content from the nearest server to the user |
| **Reduces load** | Origin server only handles dynamic requests |
| **DDoS protection** | Absorbs large volumes of traffic across many nodes |
| **Availability** | If one node fails, another takes over |

**Popular CDNs:** Cloudflare, AWS CloudFront, Akamai, Fastly

> CDNs improve **performance** and **security** — Cloudflare for example also acts as a WAF.

---

## 7. Databases

A **database** stores all the persistent data a website needs — user accounts, posts, messages, transactions.

**Two main types:**

### Relational (SQL)
Data is stored in structured tables with rows and columns.

```sql
SELECT * FROM users WHERE username = 'nicholas';
```

| Database | Notes |
|---|---|
| **MySQL** | Most common for web apps |
| **PostgreSQL** | Advanced features, highly reliable |
| **SQLite** | Lightweight, used in small apps |

### Non-Relational (NoSQL)
Data stored as flexible documents, key-value pairs, or graphs.

```json
{ "username": "nicholas", "role": "admin", "joined": "2024" }
```

| Database | Notes |
|---|---|
| **MongoDB** | Document-based, very flexible |
| **Redis** | Key-value store, used for caching and sessions |

**How a database fits in a request:**
```
Browser sends request
      ↓
Backend receives it
      ↓
Backend queries database ("Get user with ID 5")
      ↓
Database returns data
      ↓
Backend builds response and sends back to browser
```

> **SQL Injection** is the most critical database attack — it exploits unsanitised user input sent directly into SQL queries.

---

## 8. WAF — Web Application Firewall

A **WAF (Web Application Firewall)** sits between the internet and your web server, inspecting every HTTP request and blocking malicious ones before they reach the application.

```
Internet ──► WAF (inspects traffic) ──► Web Server
                    │
              Blocks attacks:
              SQL Injection
              XSS
              DDoS
              Bad bots
```

**What a WAF does:**

| Function | Description |
|---|---|
| **Filters requests** | Inspects headers, cookies, query strings, and body |
| **Blocks known attacks** | Uses rules to detect SQLi, XSS, CSRF, and more |
| **Rate limiting** | Blocks IPs sending too many requests (DDoS protection) |
| **Geo-blocking** | Can block traffic from specific countries |
| **Logging** | Records all traffic for analysis and incident response |

**WAF vs Firewall:**

| | Firewall | WAF |
|---|---|---|
| Operates at | Network layer (Layer 3/4) | Application layer (Layer 7) |
| Understands | IP addresses and ports | HTTP requests and responses |
| Protects against | Port scans, network attacks | SQLi, XSS, web app attacks |

**Popular WAFs:** Cloudflare WAF, AWS WAF, ModSecurity, Imperva

> A WAF is your **last line of defence** before a malicious request reaches your application code.

---

## 9. The Complete Picture

When you visit a website, here is everything working together:

```
You type https://www.example.com
              │
              ▼
        DNS Resolution
        (Domain → IP address)
              │
              ▼
        CDN Check
        (Is a cached copy nearby? Serve it fast)
              │
              ▼
        Load Balancer
        (Which server should handle this request?)
              │
              ▼
        WAF
        (Is this request safe? Block if malicious)
              │
              ▼
        Web Server (Apache / Nginx)
        (Receives the HTTP request)
              │
              ▼
        Backend (PHP / Python / Node.js)
        (Processes logic, queries database)
              │
              ▼
        Database (MySQL / MongoDB)
        (Returns requested data)
              │
              ▼
        Response travels back through the stack
              │
              ▼
        Your browser renders HTML + CSS + JS ✅
```

---

## 10. Study Checklist

**DNS**
- [ ] Explain the full DNS resolution journey
- [ ] Know A, MX, TXT, and CNAME records
- [ ] Understand TTL and caching

**URLs**
- [ ] Label every part of a URL
- [ ] Know the difference between HTTP and HTTPS
- [ ] Recognise URL-based attacks (phishing, open redirect)

**HTTP**
- [ ] Know all HTTP methods
- [ ] Memorise key status codes
- [ ] Understand GET vs POST and cookies

**Websites**
- [ ] Know the roles of HTML, CSS, and JavaScript
- [ ] Understand static vs dynamic websites
- [ ] Explain how a login and session works

**Infrastructure**
- [ ] Explain what a load balancer does and why it is needed
- [ ] Understand how a CDN improves speed and security
- [ ] Know the difference between SQL and NoSQL databases
- [ ] Explain what a WAF is and how it differs from a regular firewall

**Practical (Kali Linux)**
- [ ] Use `nslookup` and `dig` for DNS lookups
- [ ] Intercept HTTP requests using Burp Suite
- [ ] Inspect website requests using browser DevTools (F12)
- [ ] Practice web fundamentals rooms on TryHackMe

---

> Part of my Cybersecurity and Digital Forensics learning journey at Nkumba University
> Connect: LinkedIn | GitHub
