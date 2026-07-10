# TryHackMe: Computer Types (Computer Fundamentals Module)

**Room:** Computer Types
**Module:** Computer Fundamentals
**Difficulty:** Beginner
**Write-up by:** Nicholas Kiyimba
**Platform:** TryHackMe

## Overview

This room followed on from Inside a Computer System and moved from what makes up a single computer to the different types of computers that exist. It was framed around a short story of a character named Sophia, who notices her neighbor's smart fridge on her home WiFi and starts questioning what actually counts as a computer. I liked this framing because it made the point early that computers are no longer just laptops and phones, they are quietly built into everyday objects.

## What I Learned

* How to identify and distinguish between computers I use directly, such as laptops and smartphones
* How to identify computers I use indirectly, such as servers, IoT devices, and embedded systems
* What makes each type suited to its specific purpose

## The Computers You Sit In Front Of

The room introduced four computer types that can look similar but serve very different purposes.

| Computer Type | Screen and Keyboard | Main Purpose |
|---|---|---|
| Laptop | Yes | Portable everyday computing |
| Desktop | Yes | Sustained performance at a fixed location |
| Workstation | Yes | Precision and reliability for professional tasks |
| Server | No | Providing services to many users over a network |

Going through the story, I picked up why each of these exists rather than just memorizing the table.

A laptop is built for portability. It handles everyday tasks like emails and documents well, but being small and battery-powered makes sustained cooling difficult, so it slows down under heavy long-term load.

A desktop trades portability for consistency. Since it stays in one place and uses wall power, it can cool itself better and sustain performance over longer tasks.

A workstation looks similar to a desktop but is built differently under the hood. It prioritizes accuracy and reliability using specialized components, which matters for professional work like simulations and 3D modeling where errors during long computations are costly.

A server has no screen or keyboard at all. It runs continuously and answers requests from many users at once. I never interact with servers directly, but I now understand they are quietly powering a lot of the tools I use every day.

## The Computers Hiding in Everyday Objects

The second half of the room covered computers I do not interact with directly.

| Type | What It Is | Examples |
|---|---|---|
| Smartphone | Pocket-sized computer optimized for battery life and connectivity | iPhone, Android phone |
| Tablet | Touch-first computer with a larger screen | iPad, drawing tablet |
| IoT device | Network-connected device with a single purpose | Thermostat, smart doorbell, fitness tracker |
| Embedded computer | Computer built into another device | Coffee maker controller, automatic door sensor, lamp dimmer chip |

The distinction that stood out most to me was IoT versus embedded computing. Both can be small and single-purpose, but the difference comes down to connectivity. An IoT device connects to a network to report data or receive commands. An embedded computer might not connect to anything at all, it just does its job inside the machine, sometimes for years without anyone noticing it is there. The example of the automatic door sensor detecting movement and signaling the motor to open made this click for me, since that is something I walk past daily without a second thought.

## Why There Is No Single Best Computer

By the end of the room, the key idea tied everything together for me: every computer design is a trade-off.

* Mobility costs power, so smaller and more portable computers must sacrifice sustained performance.
* Reliability costs money, which is why servers and critical systems use redundancy such as extra power supplies and disks to avoid failure.
* Purpose shapes everything. I touch a phone directly, I ask a server for information without seeing it, and an IoT device works quietly in the background without demanding attention.

There is no single best computer, only the right tool for the job.

I finished the room by going through the attached static site to complete the interactive challenge and retrieve the flag.

## Why This Matters To Me

This room reframed how I think about computers before I even get into security concepts. I used to think of computers as things with a screen and keyboard sitting in front of me. Now I see them as a much wider category, including the servers behind the apps I use, the IoT devices reporting data on networks, and the embedded chips quietly running inside doors, appliances, and sensors. This matters for cybersecurity because every one of these types has a different attack surface, and understanding what kind of computer I am looking at is the first step to understanding how it could be secured or exploited.

## Key Takeaway

The most critical computers are not always the fastest or flashiest. Sometimes they are the silent chips that keep doors opening, planes flying, and coffee machines brewing.

---
*This write-up documents my own progress through TryHackMe as I work through the Computer Fundamentals module.*
