# DNS (DOMAIN NAME SYSTEM)

This systme provides a simple way to communicate with devices without rembering omplex IP Iddresses instead using its **name**

## TYPES OF DNS

## TOP LEVEL DNS

This is the most right hand part of the Domain name forexample TryHackme.com categories are;

**GENERIC TOP LEVEL DOMAIN (GTLD)**

This was meant ot tel the user the purpose of the domain name.forexamole **.com** for commercial purposes , **.edu** for education purposes ,**.org** for organisation. and **.gov** for government.

**CCTLD ( COUNTRY CODE TOPLEVEL DOMAIN )**

This type of DNS is used for geographical purposes e.g **.ca** for sites based in Canada, **.co.uk** for sites based in the United Kingdom e.t.c

Due to such demand, there has been an inflax of GTLD raing from .club, .website,. biz and so many more.

## SECOND LEVEL DOMAIN

Taking TryHackMe as an examole, the **.com** is the TLD and TryHackMe is the Second level domain.

**SUBDOMAIN**

That sits on the left hand sise of the second level domain. for example **admin.TryHackMe.com**. The admin part is the subdomain.  

## DNS RECORD TYPES

DNS isn't just for websites, multiple DNS  record types exist;

**A Records**

These records resolves to the IPV4 addresses to a domain name.

**AAAA Records**

These roecord resolve to the IPV6 addresseses   to a domain name.

**CNAME Records**

These records rsolve to another domain name forexample TryHackMe's onlineshop has the subdomain name store.TryHackMe.com returns a CNAME record of shops.shopify.com.
Another DNS request would be made to shops.shopify.com to work out the  IP Address.

**MX Records(Mail Exchanger Record)**

MX Record 

*What is it in simple words?*

Think of an MX record like a post office address label.
When someone sends you an email, the internet needs to know "where should this email be delivered?" — the MX record answers that question.

Simple Analogy

Imagine you run a company. You don't receive letters at your front door — you have a mailroom on the 3rd floor that handles all incoming mail.

The MX record is like the sign that says: "All mail for this company goes to the mailroom, 3rd floor."

Simple anaalogy

Someone sends email to: nicholas@example.com

         ↓
         
Internet asks DNS: "Who handles email for example.com?"

         ↓
         
DNS checks the MX Record → "mail.example.com"

         ↓
Email is delivered to mail.example.com

**TXT Record (Text Record)**

**What is it in simple words?*

A TXT record is like a sticky note attached to your domain that contains important information — mainly used for verification and security purposes.

Simple Analogy

Imagine your domain is a house. The TXT record is a notice board outside the house where you can pin important notes for anyone who needs to verify something about you.
"Yes, this house is legitimate."


"Only these people are allowed to send mail on behalf of this house."

# What Happens When You Make a DNS Request


---

## Table of Contents

1. [Simple Analogy](#simple-analogy)
2. [Step-by-Step Journey](#step-by-step-journey)
3. [The Key Players](#the-key-players)
4. [TTL — Time To Live](#ttl--time-to-live)
5. [Key Terms](#key-terms)
6. [Study Checklist](#study-checklist)

---

## Simple Analogy

Think of DNS like a phone book system. You know a person's name (google.com) but you need their phone number (IP address) to actually call them.

But instead of one phone book, there are multiple people you ask — each one knows a little more than the last.

---

## Step-by-Step Journey

Let's say you type www.google.com in your browser.

---

### Step 1 — Your Computer Checks Its Own Memory (Cache)

When you request a domain name, your computer first checks its local cache to see if you have previously looked up the address recently.

- If YES — it uses the saved IP address. No DNS request needed. Done.
- If NO — it moves to the next step.

> Like remembering a friend's number without looking it up.

---

### Step 2 — The Recursive DNS Resolver

A Recursive DNS Server is usually provided by your ISP, but you can also choose your own (e.g. Google's 8.8.8.8 or Cloudflare's 1.1.1.1).

This server also has a local cache of recently looked up domain names.

- If a result is found locally, it is sent back to your computer and your request ends here. This is common for popular and heavily requested services such as Google, Facebook, and Twitter.
- If the request cannot be found locally, a journey begins to find the correct answer, starting with the internet's root DNS servers.

> The resolver is like a librarian — it does not know everything, but it knows who to ask.

---

### Step 3 — The Root Name Server

The root servers act as the DNS backbone of the internet. Their job is to redirect you to the correct Top Level Domain (TLD) Server depending on your request.

For example, if you request www.tryhackme.com, the root server will recognise the Top Level Domain of .com and refer you to the correct TLD server that deals with .com addresses.

> Like asking: "Which city is google.com in?" — Answer: "It is in the .com city."

---

### Step 4 — The TLD Name Server

The TLD server holds records for where to find the authoritative server to answer the DNS request.

The authoritative server is often also known as the nameserver for the domain.

For example, the nameserver for tryhackme.com is kip.ns.cloudflare.com and uma.ns.cloudflare.com.

You will often find multiple nameservers for a domain name to act as a backup in case one goes down.

> Like asking: "Which street in the .com city does google live on?"

---

### Step 5 — The Authoritative Name Server

An authoritative DNS server is the server that is responsible for storing the DNS records for a particular domain name.

This is also where any updates to your domain name DNS records would be made.

Depending on the record type, the DNS record is then sent back to the Recursive DNS Server, where a local copy will be cached for future requests and then relayed back to the original client that made the request.

DNS records all come with a TTL (Time To Live) value. This value is a number represented in seconds that tells the client how long the response should be saved locally before you have to look it up again. Caching saves on having to make a DNS request every time you communicate with a server.

> This is the final authority — like reaching the exact house and reading the number on the door.

---

## The Full Picture

```
You type www.google.com
          |
          v
    Browser Cache -----------> Hit? Done immediately
          |
         Miss
          |
          v
      OS Cache ----------------> Hit? Done
          |
         Miss
          |
          v
   Recursive DNS Resolver (ISP / 8.8.8.8 / 1.1.1.1)
          |
          v
    Root Name Server --------> "Go ask the .com TLD server"
          |
          v
    TLD Name Server (.com) --> "Go ask ns1.google.com"
          |
          v
  Authoritative Name Server -> "IP = 142.250.185.46"
          |
          v
   Resolver caches the answer + sends IP to your PC
          |
          v
  Browser connects to 142.250.185.46
```

---

## The Key Players

| Player | Role |
|---|---|
| Browser / OS Cache | Checks saved answers first — fastest possible response |
| Recursive Resolver | Does the full lookup on your behalf — the librarian |
| Root Name Server | Knows where all TLD servers are — the internet's backbone |
| TLD Name Server | Handles .com, .org, .ug etc. — narrows down to the right nameserver |
| Authoritative Name Server | Holds the final, definitive DNS records for the domain |

---

## TTL — Time To Live

Every DNS record has a TTL value measured in seconds. It controls how long the answer is cached before it must be looked up again.

- TTL = 300 means cache the answer for 5 minutes
- TTL = 3600 means cache the answer for 1 hour
- TTL = 86400 means cache the answer for 24 hours

Lower TTL = more DNS queries but faster propagation of changes.
Higher TTL = fewer queries but slower updates when records change.

---

## Key Terms

| Term | Definition |
|---|---|
| DNS | Domain Name System — translates domain names to IP addresses |
| DNS Query | A question sent to a DNS server ("What is the IP of X?") |
| DNS Response | The answer returned by the DNS server |
| Recursive Resolver | A server that performs the full DNS lookup on your behalf |
| Root Name Server | Top-level DNS servers — know where all TLD servers are |
| TLD | Top-Level Domain — the .com, .org, .ug part of a domain |
| Authoritative Name Server | The final DNS server with the definitive answer for a domain |
| TTL | Time To Live — how long a DNS answer is cached in seconds |
| Cache | Saved DNS answers to avoid repeating the full lookup |

---

## Study Checklist

- [ ] Understand what DNS is and why it exists
- [ ] Be able to explain each step of the DNS resolution journey
- [ ] Know the difference between a recursive resolver and an authoritative name server
- [ ] Understand what TTL is and how caching works
- [ ] Practice DNS lookups using nslookup or dig on Kali Linux
- [ ] Look up a real domain's DNS records using MXToolbox

