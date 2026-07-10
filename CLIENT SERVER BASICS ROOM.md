# TryHackMe: Client-Server Basics (Computer Fundamentals Module)

**Room:** Client-Server Basics
**Module:** Computer Fundamentals
**Difficulty:** Beginner
**Write-up by:** Nicholas Kiyimba
**Platform:** TryHackMe

## Overview

In the previous rooms I looked at the types of computers that exist and how they are used. Most of that was about computers working alone, storing their own files and running their own programs without talking to anyone else. This room picked up from there and explained how computers stopped working in isolation and started communicating with each other, eventually leading to the internet as we know it.

I learned that early networks such as ARPANET, CYCLADES, NPL, and NSFNET were the precursors that paved the way for the modern internet, and that once systems became interconnected they began to specialize, similar to how people in society each offer their own set of skills as a service.

## What I Learned

* The Client-Server model
* DNS, Client, Server, Port, Protocol, and Network on a surface level

## The Client-Server Model, Explained With Pizza

The room used a pizza takeaway analogy to explain the client-server model, and it made the concept click for me immediately.

Alice wants pizza. She tells Bob what she wants, Bob drives to Luigi's Pizza, places the order, and brings the pizza back. Mapped onto computer systems:

* Alice is the client. In computing terms this is something like a browser.
* Bob delivers the request. This role is closer to a protocol.
* Luigi's Pizza is the server, the system that fulfills the request.

A few things stood out to me from this analogy.

**Client and Server:** The client is always the one who initiates the request, never the server. Alice requests, Luigi's responds. In web terms, a browser requests a webpage and a server serves it.

**Request and Response:** Alice's request goes through Bob to Luigi's, not directly. If the request is malformed or the item is unavailable, an error response comes back instead, such as Bob returning to say there is no pepperoni pizza left. The same applies to computer systems, where a badly formatted or unavailable request results in an error response rather than the expected content.

**Protocol:** Bob acts like a protocol. A protocol defines which commands a client and server understand, how a request must be structured, what syntax to use, what response to expect for a valid request, and what response to expect for a faulty one. This is the shared language that makes the whole exchange possible.

**Port:** A port identifies a specific service running on a server, similar to Luigi's using different doors for takeaway, dine-in, and delivery. A single server can run multiple services at once, and each one is reached through its own port.

**DNS:** Just like Bob needed a GPS to find Luigi's Pizza once he only had the name, DNS (Domain Name Service) resolves a name such as a website into the server's actual location, known as an IP address. I found it useful to think of an IP address the same way I would think of a home address, since it tells you exactly where to deliver the request.

## HTTP and the GET Method

The second part of the room moved from the general client-server model into HTTP specifically, the protocol used for the World Wide Web.

I learned that HTTP is stateless, meaning each request is handled independently and the server does not remember previous requests on its own. What makes logins and sessions feel continuous is something built on top of HTTP at the application level, such as a session identifier stored in a cookie or token that gets sent with every request after I log in. Without that mechanism, I would have to log in again on every single request.

HTTP defines 9 core methods, referred to as methods rather than commands: GET, POST, PUT, DELETE, PATCH, HEAD, OPTIONS, CONNECT, and TRACE. The room focused on GET, which retrieves a resource from a web server.

I worked through this practically using the lab machine. I opened Firefox, navigated to a local demo website, and used the Developer Tools Network tab to inspect the actual GET requests my browser was sending. A few fields stood out as I looked at a captured request:

* **Scheme:** whether HTTP or HTTPS was used
* **Host:** the name of the server I requested resources from
* **Filename:** the specific resource requested, where "/" translates to "index.html"
* **Address:** the IP address the site is hosted on, in this case 127.0.0.1 since the site was hosted locally
* **Status:** whether the request succeeded, shown here as a 200 OK

I also looked at the response itself, which splits into a response header containing metadata and a response body containing the actual content, in this case the HTML of the index page.

## Why This Matters To Me

This room connected a lot of things I already used daily, like typing a website address into a browser, to what is actually happening behind the scenes. Understanding the client-server model, ports, protocols, and how HTTP requests and responses are structured gives me a base to build on for web application security later, since most web attacks are really just abuses of this same request and response flow.

## Key Takeaway

The client always initiates, the server always responds, and everything in between, ports, protocols, and DNS, exists to make sure the right request reaches the right service and gets back to the right place.

---
*This write-up documents my own progress through TryHackMe as I work through the Computer Fundamentals module.*
