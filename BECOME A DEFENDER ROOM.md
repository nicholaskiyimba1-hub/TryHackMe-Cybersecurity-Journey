# BECOME A DEFENDER ROOM

## Introduction

This room introduced me to **defensive security** and the role of defenders, commonly referred to as the **Blue Team**.

In the previous room, *Become a Hacker*, I approached security from an offensive perspective by looking for weaknesses and exploiting them in an authorized lab. This room gave me the other side of the picture: understanding what needs to be protected, gaining visibility into an environment, applying security controls, and responding to threats.

A major idea throughout this room was that effective defense starts with understanding the environment. A defender cannot properly protect systems they do not know exist.

---

# Task 1 — What Is Defensive Security?

## What I learned

**Defensive Security** focuses on protecting systems, data, users, and infrastructure from attacks.

Defenders work to:

- Prevent attacks where possible
- Detect suspicious or malicious activity
- Reduce the impact of attacks
- Investigate security incidents
- Respond to threats
- Improve security controls after incidents

Defensive security is closely connected to the **CIA Triad**:

- **Confidentiality** — protecting information from unauthorized access
- **Integrity** — ensuring information is not improperly modified
- **Availability** — ensuring systems and information remain accessible when needed

## The Blue Team

Defensive security professionals are commonly referred to as the **Blue Team**.

A defender needs to understand how attackers think because knowing the likely attack paths helps defenders identify where stronger protections and monitoring are needed.

### My takeaway

Coming directly from the *Become a Hacker* room, I found the connection between offensive and defensive security important.

An attacker asks:

> "How can I get into this system?"

A defender needs to ask:

> "How could someone get into this system, and how can I prevent or detect it?"

---

# Task 2 — Understanding Your Environment

Before protecting an environment, a defender needs to understand what exists inside it.

The room used a **city analogy** to make this easier to understand.

## City Analogy

| Defensive Security Concept | City Analogy |
|---|---|
| Employee devices | Homes |
| Web server | Shops/public buildings |
| Mail server | Post office |
| Firewall | City gate |
| Internet | Everything outside the city |
| Logs and monitoring | Cameras and reports |
| Suspicious activity | Suspicious behavior around the city |

The analogy helped me understand that defenders need visibility into their environment just like city authorities need to know what exists in their city.

---

## Core Defensive Security Activities

### Prevention

Prevention means putting security controls in place to stop attacks before they cause damage.

Examples include:

- Firewalls
- Antivirus/endpoint protection
- Regular software updates
- Access restrictions

### Detection

Detection involves monitoring systems and networks to identify suspicious activity.

Examples include:

- Logs
- Security alerts
- Network monitoring
- Endpoint monitoring

### Mitigation

Mitigation focuses on limiting the impact of a threat after it has been identified.

Examples include:

- Blocking malicious traffic
- Isolating affected systems
- Disabling compromised accounts

### Analysis

Analysis involves investigating what happened and determining:

- How the incident occurred
- Which systems were affected
- What evidence is available
- What the attacker may have accessed

### Response and Improvement

After an incident, defenders need to respond, recover, and improve security controls so that similar incidents are less likely to succeed in the future.

---

# Understanding Client Infrastructure

A defender's scope is limited to the organization's or client's environment.

Some common infrastructure components include:

| Component | Purpose |
|---|---|
| **Employee Devices** | Used by employees to work and access company resources |
| **Web Server** | Hosts websites and web applications |
| **Mail Server** | Sends and receives organizational email |
| **Firewall** | Controls allowed network traffic |
| **Internet** | External networks outside the organization's direct control |

The exercise required me to explore the simulated city and map the different parts of the city to their corresponding infrastructure components.

### My takeaway

This task reinforced the importance of **visibility**.

If a defender does not know what systems, services, users, or connections exist, it becomes much harder to secure the environment effectively.

---

# Task 3 — Defending Your Environment

After mapping the environment, the next step was to actually defend it.

## The Defender Mindset

A defender should not treat every system as an isolated component. Systems are interconnected, meaning an attacker who compromises one system may be able to use it as a stepping stone toward another.

For example:

```text
Malicious Email
      ↓
Employee Workstation
      ↓
Stolen Credentials
      ↓
Mail Server
      ↓
Sensitive Data
```

Each stage provides an opportunity for a defender to detect or stop the attack.

---

## Key Defender Principles

### 1. Threat Anticipation

Defenders should think about realistic ways an attacker could target the environment.

The question I found useful here was:

> "What if?"

Instead of assuming everything will work as intended, defenders should consider what could go wrong.

### 2. Attack Awareness

Many attacks follow recognizable stages and patterns.

Understanding common attack techniques and attack chains helps defenders identify suspicious activity earlier.

### 3. Risk Prioritization

Not every system has the same importance or risk.

Defenders need to identify the systems and assets that would have the greatest impact if compromised and focus security efforts accordingly.

This is the principle that focuses on identifying the most critical systems and guiding security efforts.

### 4. Continuous Adaptation

Security is not something that can be configured once and forgotten.

Threats change, vulnerabilities are discovered, and attackers develop new techniques.

Defenses therefore need to be continuously reviewed and improved.

---

# Security Controls

The room compared defensive controls to protections used in a city.

There is no single security control that can stop every attack. Instead, defenders use **layered security**.

## Employee Devices

### Possible threat

A user could click a malicious link or download unsafe software.

### Possible defenses

- Antivirus/endpoint protection
- Regular software updates
- User awareness

---

## Web Server

### Possible threat

Attackers could attempt to compromise the website or application.

### Possible defenses

- Restricting allowed traffic
- Secure communication
- Proper system and application configuration

---

## Mail Server

### Possible threat

Attackers could send malicious or deceptive emails.

### Possible defenses

- Spam filtering
- Attachment scanning
- Email security controls

---

## Firewall

### Possible threat

Untrusted systems on the internet could attempt to access internal resources.

### Possible defenses

- Firewall rules
- Restricting unnecessary access
- Blocking known malicious sources

---

## External Internet

### Possible threat

Threats can originate from outside the organization's network.

### Possible defenses

- Restrict inbound connections
- Monitor network activity
- Detect suspicious behavior

---

# Mapping and Defending the City

The hands-on exercises required me to:

1. Identify the different parts of the simulated environment.
2. Map them to real-world infrastructure.
3. Understand what each component does.
4. Identify possible risks.
5. Apply appropriate defensive controls.
6. Successfully defend the simulated infrastructure.

These exercises helped turn the theoretical concepts into something more practical.

---

# Task 4 — Where to Go From Here

This room gave me a high-level introduction to defensive cybersecurity and showed me how defenders approach an environment.

## Key Terminology

### Blue Team

A group of cybersecurity professionals responsible for defending systems and responding to threats.

### Client Infrastructure

The networks, servers, devices, applications, and other systems belonging to an organization.

### Visibility

The ability to monitor and understand activity occurring across systems and networks.

### Threat

A potential source of harm to systems, users, or data.

### Prevention

Security measures designed to stop threats before they cause harm.

### Detection

Identifying suspicious or malicious activity.

### Mitigation

Reducing the impact of a threat after it has been identified.

### Risk

The likelihood and potential impact of a threat causing harm to an organization.

---

# Defensive Security Career Paths

This room introduced several areas where defensive security knowledge can be applied.

## Security Operations Center (SOC)

SOC analysts monitor systems, investigate alerts, and look for suspicious activity.

## Threat Intelligence

Threat intelligence involves researching threats, attackers, techniques, and trends to help organizations prepare their defenses.

## Digital Forensics and Incident Response (DFIR)

DFIR involves investigating security incidents to understand what happened, contain threats, and help organizations recover.

---

# What I Learned From This Room

The biggest lesson from this room was that **defensive security begins with visibility**.

Before I can defend an environment, I need to understand:

- What systems exist
- Who uses them
- How they communicate
- What services they provide
- Which systems contain valuable information
- What could go wrong
- How an attacker might move through the environment

I also learned that security should be layered. A firewall alone is not enough. Endpoint protection alone is not enough. Monitoring alone is not enough.

A stronger defensive strategy combines multiple controls:

```text
Prevention
    ↓
Detection
    ↓
Analysis
    ↓
Mitigation
    ↓
Response
    ↓
Improvement
```

This creates a continuous defensive process rather than a one-time configuration.

---

# Connection With Become a Hacker

The two rooms helped me see both sides of cybersecurity.

| Offensive Security | Defensive Security |
|---|---|
| Looks for weaknesses | Protects against weaknesses |
| Thinks like an attacker | Thinks about how attacks can be stopped |
| Enumerates systems | Maintains visibility over systems |
| Exploits vulnerabilities | Patches and mitigates vulnerabilities |
| Attempts to gain access | Detects and prevents unauthorized access |
| Tests security controls | Builds and improves security controls |

Understanding both perspectives is valuable because defenders need to understand how attacks work in order to detect and prevent them.

---

# My Overall Experience

I found this room useful because it changed my perspective from simply asking **"How can I attack this?"** to also asking **"How would I protect this?"**

The city analogy made the concept of infrastructure easier to understand. I could see how employee computers, servers, firewalls, mail systems, and external networks all form part of one environment that needs to be monitored and protected.

The hands-on exercises also showed me that defensive security is not just about installing security software. It involves understanding the environment, prioritizing risk, applying controls, monitoring activity, and continuously adapting to new threats.

---

# Key Takeaways

- Defensive security focuses on preventing, detecting, and responding to threats.
- The Blue Team is responsible for defending systems and investigating suspicious activity.
- Visibility is fundamental to effective defense.
- Defenders need to understand the infrastructure they are responsible for protecting.
- Prevention, detection, mitigation, analysis, and response work together.
- Attackers can move from one compromised system to another, so defenders must consider the environment as an interconnected system.
- Risk prioritization helps defenders focus resources on the most critical systems.
- Layered security is stronger than relying on a single defensive control.
- Defensive security is a continuous process because threats and attack techniques evolve.

---

# Final Reflection

Completing **Become a Defender** gave me a better understanding of the defensive side of cybersecurity.

After completing **Become a Hacker**, I had started looking at systems from the attacker's perspective. This room helped me balance that knowledge by understanding how a defender can identify important assets, monitor an environment, anticipate attack paths, and apply security controls.

This also marks an important point in my **Pre Security** learning journey because I now have an introductory understanding of both offensive and defensive security.

My next step is to continue building these foundations through more hands-on cybersecurity practice and gradually move into deeper areas such as SOC operations, penetration testing, digital forensics, incident response, and security analysis.
