# HTTP (HYPER TEXT TRANSFER PROTOCOL)

This refers to a set of rules used for communication with the web servers for transmiting of web page data whether imgages, and vidoess  

## HTTPS (HYPER TEXT TRANSFER PROTOCOL SECURE)

This is the secure version of the **HTTP** through encryption. On top of  providing a secure connection, it also provides assurenece that the user is accessing the actual requsted page.

# 🔗 URLs — Uniform Resource Locators

**Author:** Nicholas Kiyimba | BSc Cybersecurity & Digital Forensics — Nkumba University
**Topic:** URL Structure & Cybersecurity Relevance
**Source:** TryHackMe + Personal Study Notes
**Last Updated:** June 2026

---

## What is a URL?

A **URL (Uniform Resource Locator)** is the full address you type into a browser to visit a specific place on the internet.

> Like a physical address — it tells your browser exactly where to go and how to get there.

---

## Anatomy of a URL

```
https://www.tryhackme.com:443/room/dns?search=dns&page=2#results
  │        │        │      │    │              │            │
Protocol Subdomain Domain Port Path         Query        Fragment
```

| Part | Example | Purpose |
|---|---|---|
| **Protocol** | `https://` | How to communicate with the server |
| **Subdomain** | `www.` | Which section or server of the site |
| **Domain** | `tryhackme.com` | The main registered address |
| **Port** | `:443` | Which door to connect through |
| **Path** | `/room/dns` | Which specific page or resource |
| **Query** | `?search=dns&page=2` | Extra filters sent to the server |
| **Fragment** | `#results` | Jump to a section within the page (browser only) |

---

## Key Parts Explained

### Protocol
Defines how the browser communicates with the server.

| Protocol | Use |
|---|---|
| `http://` | Unencrypted web traffic |
| `https://` | Encrypted with TLS — secure |
| `ftp://` | File transfers |
| `ssh://` | Secure remote access |

### Subdomain
Sits before the main domain and points to a specific server or section.
Common examples: `www`, `mail`, `api`, `admin`, `blog`

### Port
Acts like a door number. Usually hidden because browsers fill it in automatically.

| Port | Service |
|---|---|
| 80 | HTTP |
| 443 | HTTPS |
| 22 | SSH |
| 53 | DNS |
| 21 | FTP |

### Query Parameters
Start with `?` and pass extra data to the server.
```
?search=dns&page=2
 └─ key=value pairs separated by &
```

---

## HTTP vs HTTPS

```
HTTP  → Data travels in PLAINTEXT → vulnerable to interception
HTTPS → Data is ENCRYPTED with TLS → safe for sensitive data
```

> Always look for HTTPS and the padlock icon. HTTP is a red flag in cybersecurity.

---

## URL-Based Attacks

| Attack | Description |
|---|---|
| **Phishing** | Fake URLs mimicking real ones e.g. `paypa1.com` vs `paypal.com` |
| **Open Redirect** | `example.com/redirect?url=evil.com` silently sends you to a malicious site |
| **SQL Injection** | Malicious code injected via query params e.g. `?id=1' OR '1'='1` |
| **Directory Traversal** | Path manipulation to access restricted files e.g. `/../../../etc/passwd` |
| **URL Spoofing** | Hiding malicious links behind legitimate-looking anchor text |

---

## Study Checklist

- [ ] Be able to label every part of a URL
- [ ] Know the difference between HTTP and HTTPS
- [ ] Understand what ports are and why they matter
- [ ] Recognise common URL-based attack patterns
- [ ] Practice inspecting URLs on TryHackMe rooms

---

# 📡 Making a Request — HTTP Requests & Responses

**Author:** Nicholas Ssemakula | BSc Cybersecurity & Digital Forensics — Nkumba University
**Topic:** HTTP Request & Response Cycle
**Source:** TryHackMe + Personal Study Notes
**Last Updated:** June 2026

---

## What is a Request?

When you type a URL and press Enter, your browser sends an **HTTP request** to a web server. The server sends back a **response**.

```
CLIENT (Browser) ──── HTTP REQUEST ────> SERVER
CLIENT (Browser) <─── HTTP RESPONSE ─── SERVER
```

> Like ordering food — you place an order (request), the kitchen prepares it and sends it back (response).

---

## A Raw HTTP Request

```
GET /index.html HTTP/1.1
Host: www.tryhackme.com
User-Agent: Mozilla/5.0
Accept-Language: en-US
Cookie: session=abc123
```

| Part | Example | Meaning |
|---|---|---|
| **Method** | `GET` | What action you want |
| **Path** | `/index.html` | Which resource you want |
| **HTTP Version** | `HTTP/1.1` | Protocol version |
| **Headers** | `Host`, `Cookie` etc. | Extra metadata |

---

## HTTP Methods

| Method | Action |
|---|---|
| **GET** | Fetch / retrieve data |
| **POST** | Send data to the server |
| **PUT** | Update existing data |
| **DELETE** | Remove data |
| **PATCH** | Partially update data |

> GET and POST are the most important to understand first.

---

## Common Request Headers

| Header | Purpose |
|---|---|
| `Host` | Which website you are requesting |
| `User-Agent` | Identifies your browser and OS |
| `Cookie` | Sends saved cookies to the server |
| `Authorization` | Sends credentials or tokens |
| `Content-Type` | Type of data being sent in the body |
| `Referer` | The page you came from |

---

## HTTP Response

```
HTTP/1.1 200 OK
Content-Type: text/html
Set-Cookie: session=abc123; HttpOnly

<!DOCTYPE html>
<html><body>Welcome</body></html>
```

---

## Status Codes

| Range | Meaning |
|---|---|
| **2xx** | Success |
| **3xx** | Redirect |
| **4xx** | Client error (your fault) |
| **5xx** | Server error (server's fault) |

### Most Important Ones

| Code | Meaning |
|---|---|
| **200** | OK — success |
| **201** | Created — new resource made |
| **301** | Moved Permanently |
| **302** | Temporary Redirect |
| **400** | Bad Request |
| **401** | Unauthorised — login required |
| **403** | Forbidden — no permission |
| **404** | Not Found |
| **500** | Internal Server Error |

---

## GET vs POST

| | GET | POST |
|---|---|---|
| Data location | In the URL | In the request body |
| Visible | Yes — in address bar | No — hidden |
| Bookmarkable | Yes | No |
| Use for | Fetching pages, searching | Login forms, file uploads |
| Safe for passwords | No | Yes |

---

## Cookies

HTTP is **stateless** — the server forgets you after every request. Cookies solve this.

```
Server sends:  Set-Cookie: session=abc123; HttpOnly; Secure
Browser stores it and sends it automatically on every request
Server reads:  Cookie: session=abc123 → "This user is logged in"
```

| Flag | Meaning |
|---|---|
| **HttpOnly** | JavaScript cannot access the cookie — prevents XSS theft |
| **Secure** | Only sent over HTTPS |
| **SameSite** | Prevents cross-site request forgery (CSRF) |

---

## Full Request Cycle

```
1. You type https://tryhackme.com
2. DNS resolves domain to IP address
3. Browser opens TCP connection (port 443)
4. TLS handshake — encryption established
5. Browser sends HTTP GET request
6. Server processes and responds with 200 OK + HTML
7. Browser renders the page
```

---

## Security Relevance

| Attack | What It Exploits |
|---|---|
| **SQL Injection** | Query parameters or POST body |
| **XSS** | Response content rendered in browser |
| **CSRF** | Cookies sent automatically with requests |
| **IDOR** | Manipulating path or parameters to access others' data |
| **Man-in-the-Middle** | Intercepting unencrypted HTTP traffic |

---

## Study Checklist

- [ ] Understand the difference between a request and a response
- [ ] Know all HTTP methods and when to use them
- [ ] Memorise the key status codes
- [ ] Understand the difference between GET and POST
- [ ] Know what cookies are and the security flags
- [ ] Intercept a real HTTP request using Burp Suite on Kali Linux

---

> Part of my Cybersecurity and Digital Forensics learning journey at Nkumba University
> Connect: LinkedIn | GitHub
