# TryHackMe: Inside a Computer System (Computer Fundamentals Module)

**Room:** Inside a Computer System
**Module:** Computer Fundamentals
**Difficulty:** Beginner
**Write-up by:** Nicholas Kiyimba
**Platform:** TryHackMe

## Overview

This was the first room I completed in the Computer Fundamentals module. Before jumping into security concepts, I wanted to build a solid foundation in what a computer system actually is and how its core components work together. The room uses a simple analogy that stuck with me: you cannot defend a castle you have never seen, and in the same way you cannot secure a system you do not understand.

## What I Learned

* How to recognize the core building blocks of a computer system
* The function of each component
* The boot sequence a computer goes through before it becomes usable

## Core Components

The room compares PC components to parts of the human body to make the concepts easier to grasp. I worked through this using the interactive static site provided in the room, going component by component and mapping each one to its role in the system.

## The Boot Sequence

Once I understood the core components, the next part covered how a system boots. I broke this down into five steps as I went through it, again using the human body as an analogy.

**Step 1: Press the Power Button**
Power is sent to the PSU, allowing electricity to flow through the system. I found the comparison to the body waking up and receiving oxygen a helpful way to visualize it.

**Step 2: Firmware Starts**
The system's firmware begins running. This is managed by the Unified Extensible Firmware Interface (UEFI), the modern replacement for the older BIOS. I noted that UEFI is still often referred to as BIOS out of habit, but functionally they serve the same purpose.

**Step 3: Power On Self Test (POST)**
UEFI runs the Power On Self Test, checking that every required component is present, correctly configured, and functioning before continuing.

**Step 4: Select Boot Device**
UEFI holds an ordered list of devices to check for a bootable Operating System, and selects the first valid one.

**Step 5: Initiate Bootloader**
The bootloader on the selected device loads the Operating System into RAM. Once this is complete, UEFI hands control of the system over to the OS.

I then completed the static site exercise to retrieve the flag for this room.

## Why This Matters To Me

This room was light on technical depth, but I can already tell the concepts will come up again as I go deeper into cybersecurity. The boot process especially stood out to me, since I now understand it is a common target for attackers, who can compromise a system before the OS and its security controls are even active. Going through this gave me a clearer base for topics I expect to meet later, such as malware persistence, rootkits, and firmware attacks.

## Flag

```
THM{pc5ucce55fully5t4rt3d}
```

## Key Takeaway

Security starts with understanding the system, not the attack. Every layer of a computer, from the power button to the operating system, is a potential point of interest for both defenders and attackers.

---
*This write-up documents my own progress through TryHackMe as I work through the Computer Fundamentals module.*
