# 🌍 How Websites Work

**Author:** Nicholas Kiyimba| BSc Cybersecurity & Digital Forensics — Nkumba University
**Topic:** Website Structure, Stack & Security
**Source:** TryHackMe + Personal Study Notes
**Last Updated:** June 2026

---

## The Three Building Blocks

Every website is built from three core technologies:

| Layer | Technology | Role |
|---|---|---|
| **Structure** | HTML | The content and skeleton of the page |
| **Design** | CSS | How everything looks — colours, fonts, layout |
| **Behaviour** | JavaScript | Makes the page interactive and dynamic |

```
HTML  →  "There is a button here"
CSS   →  "The button is blue and rounded"
JS    →  "When clicked, show a popup"
```

---

## What Happens When You Visit a Website

```
1. You type https://tryhackme.com
2. DNS resolves domain → IP address
3. Browser connects to server (TCP + TLS handshake)
4. Browser sends HTTP GET request
5. Server responds with HTML file (200 OK)
6. Browser reads HTML → finds CSS, JS, image files
7. Browser sends more requests for those files
8. Browser assembles everything → renders the page ✅
```

---

## Static vs Dynamic Websites

### Static
Server sends the same pre-written files to everyone.
- No database needed
- Fast and simple
- Examples: portfolios, documentation

### Dynamic
Server generates a custom page per user based on a database query.
- Powered by a backend language
- Connected to a database
- Examples: Gmail, Facebook, TryHackMe, online banking

---

## The Full Stack

```
┌──────────────────────────────────┐
│  FRONTEND — HTML + CSS + JS      │  ← Runs in your browser
├──────────────────────────────────┤
│  BACKEND — PHP / Python / Node   │  ← Logic on the server
├──────────────────────────────────┤
│  DATABASE — MySQL / MongoDB      │  ← Stores all data
└──────────────────────────────────┘
```

---

## Web Servers

Software that listens for HTTP requests and sends back responses.

| Server | Notes |
|---|---|
| **Apache** | Most common, open source |
| **Nginx** | Fast and lightweight |
| **IIS** | Microsoft / Windows servers |
| **Node.js** | JavaScript-based server |

---

## How a Login Works

```
1. You submit username + password via POST request
2. Server queries database — does this user exist?
3. Server checks the password hash
4. If correct → server creates a session
5. Server sends Set-Cookie: session=abc123
6. Browser stores and sends cookie on every request
7. Server recognises you as logged in ✅
```

---

## Common Web Vulnerabilities

| Vulnerability | What Gets Exploited |
|---|---|
| **SQL Injection** | User input injected into database queries |
| **XSS** | JavaScript injected into HTML responses |
| **CSRF** | Cookies sent automatically with forged requests |
| **IDOR** | Predictable IDs used to access others' data |
| **Broken Authentication** | Weak session or password handling |
| **File Inclusion** | Server loading unintended files |

---

## Study Checklist

- [ ] Understand the roles of HTML, CSS, and JavaScript
- [ ] Know the difference between static and dynamic websites
- [ ] Be able to explain the full request-to-render journey
- [ ] Understand what a web server and database do
- [ ] Know how a login and session works
- [ ] Recognise common web vulnerabilities on TryHackMe

---

> Part of my Cybersecurity and Digital Forensics learning journey at Nkumba University
> Connect: LinkedIn | GitHub
