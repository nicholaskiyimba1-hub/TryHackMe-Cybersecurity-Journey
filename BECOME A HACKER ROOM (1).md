# BECOME A HACKER ROOM

## Introduction

This room was my first practical introduction to thinking from an offensive security perspective. Instead of only learning how systems are supposed to work, I started asking how a system could behave unexpectedly and where weaknesses might exist.

The room focused on ethical hacking in a controlled environment. I learned how security testers identify exposed functionality, enumerate web content, discover weak credentials, and understand how multiple small weaknesses can be chained together.

> **Important:** Everything in this write-up was performed against the authorized TryHackMe lab environment.

---

## Task 1 — What Is Offensive Security?

### What I learned

**Offensive Security** is the proactive testing of systems by attempting to identify and exploit weaknesses before real attackers can abuse them.

The main idea is to think from an attacker's perspective:

- What is exposed?
- What can be accessed?
- What assumptions does the application make?
- What happens when unexpected input is provided?
- Can small weaknesses be combined into a larger security issue?

In ethical hacking, these activities must be performed with **permission** and within a clearly defined **scope**.

### Key terminology

| Term | Meaning |
|---|---|
| **Red Teaming** | An authorized simulation of a real adversary to test an organization's defenses |
| **Penetration Test** | A structured assessment where an authorized tester identifies and attempts to exploit vulnerabilities |
| **Vulnerability** | A weakness or flaw that could be abused by an attacker |
| **Exploit** | A technique used to take advantage of a vulnerability |
| **Scope** | The systems, applications, and actions that are authorized to be tested |

### My takeaway

The biggest thing I took from this task is that ethical hacking is not simply about "breaking into things." It is a structured process of finding weaknesses so that they can be fixed before malicious attackers find them.

---

# Task 2 — Finding Weaknesses

## Discovering hidden web pages manually

The target application was:

```text
http://www.onlineshop.thm/
```

I was given several possible page names to investigate:

- `sitemap`
- `mail`
- `register`
- `login`
- `admin`

I tested these by adding them to the end of the URL.

Most of the incorrect pages returned an **HTTP 404 Not Found** response.

The hidden page I discovered was:

```text
/login
```

This led to the application's login page.

### What this taught me

A page does not necessarily have to be linked from the main website to be accessible. If a developer leaves a sensitive page publicly reachable, an attacker may be able to discover it through enumeration.

---

## Using Gobuster

Manually testing a few URLs works when the list is small, but it becomes inefficient when there are hundreds or thousands of possible paths.

For this reason, I used **Gobuster** to automate directory and file discovery.

### Command

```bash
gobuster dir --url http://www.onlineshop.thm/ -w /usr/share/wordlists/dirbuster/directory-list.txt
```

### Breaking down the command

- `gobuster` — starts the Gobuster tool
- `dir` — uses directory/file enumeration mode
- `--url http://www.onlineshop.thm/` — specifies the target
- `-w /usr/share/wordlists/dirbuster/directory-list.txt` — specifies the wordlist used for enumeration

The scan confirmed the `/login` page.

The status code returned for the discovered page was:

```text
200
```

An HTTP **200 OK** response indicates that the requested resource was successfully returned.

### My finding

**Hidden page:** `/login`

**Status code:** `200`

---

# Task 3 — Exploiting Weaknesses

Finding a hidden login page was only the first step. The next step was to determine whether the authentication mechanism could be abused.

This introduced an important offensive security concept: **chaining weaknesses**.

A hidden login page by itself might not be a critical vulnerability. However, if the login system also accepts a weak password, the two weaknesses can be combined to gain unauthorized access.

## Thinking like a hacker

Some questions I learned to ask are:

- What if a feature does not behave as expected?
- What inputs might the developer not have considered?
- Can a small weakness be combined with another weakness?
- What could an attacker do after gaining authenticated access?

This mindset is important in penetration testing because attackers rarely look at vulnerabilities in isolation.

---

## Manual password testing

The username `admin` is a common username, so I tested it against the provided common passwords:

```text
abc123
123456
password
qwerty
654321
```

The working credentials were:

```text
Username: admin
Password: qwerty
```

This allowed me to access the private section of the web application.

The secret message displayed after logging in was:

```text
THM{born_to_hack!}
```

> **Note:** Some older write-ups of this room show the secret as `born_to_be_a_hacker`. The current room material/results I followed use `THM{born_to_hack!}`.

---

## Automating the attack with Hydra

Manually testing a few passwords is manageable, but a real wordlist could contain hundreds, thousands, or more entries.

**Hydra** can automate password testing against supported authentication services.

The command used in the TryHackMe lab was:

```bash
hydra -l admin -P passlist.txt www.onlineshop.thm http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect" -V
```

### Command breakdown

- `hydra` — starts Hydra
- `-l admin` — specifies the username to test
- `-P passlist.txt` — specifies the password wordlist
- `www.onlineshop.thm` — specifies the target host
- `http-post-form` — tells Hydra that the login uses an HTTP POST form
- `"/login:username=^USER^&password=^PASS^:F=incorrect"` — defines the login request and the condition used to identify failed attempts
- `-V` — enables verbose output

The successful credentials identified by Hydra were:

```text
admin:qwerty
```

### Hydra result

The room's Hydra output showed **17 failed password attempts** before the correct password was found.

### Final findings

| Question | Answer |
|---|---|
| Admin password | `qwerty` |
| Secret message | `THM{born_to_hack!}` |
| Failed attempts before success | `17` |

---

# Task 4 — Where to Go From Here

This room introduced me to several fundamental offensive security concepts and gave me practical experience with web enumeration and password testing.

## Key terminology I learned

### Scope

The exact systems, applications, and actions that are authorized during a security assessment.

### Vulnerability

A weakness in a system that could potentially be abused by an attacker.

### Exploit

A technique or method used to take advantage of a vulnerability.

### Enumeration

The process of collecting information about a target to identify possible attack surfaces and weaknesses.

### Credentials

Authentication information such as usernames and passwords.

### Authentication

The process of verifying that a user or system is who it claims to be.

### Dictionary Attack

An attack that tests passwords or other values from a predefined wordlist.

---

# What I Learned From This Room

This room was important because it moved me from simply learning cybersecurity concepts to actually applying an attacker's mindset.

The main lessons I took away were:

1. **Think like an attacker.**  
   I need to question how a system could be misused instead of only considering how it was designed to work.

2. **Enumeration is important.**  
   The `/login` page was not obvious from the main website, but simple enumeration revealed it.

3. **Automation saves time.**  
   Gobuster made web-content discovery much faster than manually testing large numbers of possible paths.

4. **Weak credentials can have serious consequences.**  
   Once the hidden login page was discovered, the weak `admin:qwerty` credentials provided a path into the private area.

5. **Weaknesses can be chained.**  
   The hidden login page and weak password became much more significant when combined.

6. **Permission matters.**  
   The techniques I practiced are appropriate only when performed against systems where testing is explicitly authorized.

---

# My Overall Experience

This was one of the first rooms where I could clearly see how the concepts I had been learning about networking and web technologies connect to offensive security.

At first, the commands such as Gobuster and Hydra looked more complicated than the actual objective. After breaking the commands down, I could understand what each part was doing and why the tools were useful.

The biggest lesson for me was not simply finding the password. It was learning the process:

```text
Reconnaissance
     ↓
Enumeration
     ↓
Identify a weakness
     ↓
Test the weakness
     ↓
Gain access
     ↓
Understand the impact
```

This gave me a better picture of what penetration testing looks like at a basic level.

---

# Tools Used

- **Web Browser** — manually tested potential web pages
- **Gobuster** — automated web directory/file enumeration
- **Hydra** — automated password testing in the authorized lab
- **TryHackMe** — provided the controlled environment for the exercise

---

# Key Takeaways

- Offensive security is proactive security testing.
- Ethical hacking requires authorization and a defined scope.
- Hidden functionality can increase an application's attack surface.
- Enumeration helps uncover exposed resources.
- Gobuster can automate web-content discovery.
- Weak credentials can turn a seemingly minor issue into a larger security problem.
- Hydra can automate dictionary-based authentication testing.
- Successful penetration testing requires understanding how weaknesses can be chained together.

---

## Next Steps

After completing this room, I can continue building my offensive security foundation through more hands-on practice and gradually move toward areas such as:

- Web application security
- Penetration testing
- Vulnerability assessment
- Red teaming
- Security tooling
- Defensive security

The important thing for me is to keep practicing consistently and build the understanding behind the tools rather than simply memorizing commands.
