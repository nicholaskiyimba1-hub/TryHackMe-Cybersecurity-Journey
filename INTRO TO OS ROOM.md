# Operating Systems Introduction

**Platform:** TryHackMe  
**Module:** Operating System Basics  
**Room:** Operating Systems Introduction  
**Status:** ✅ Completed

---

# Objective

This room introduced the operating system (OS), the software layer that sits between users, applications, and computer hardware. It explained how an OS manages system resources, enforces security, and provides interfaces for interacting with the computer.

The practical exercise involved investigating a second-hand Ubuntu machine to identify its operating system, hardware specifications, filesystem, and user data.

---

# Learning Outcomes

After completing this room, I can:

- Explain the role of an operating system.
- Describe the difference between Kernel Space and User Space.
- Identify the major responsibilities of an operating system.
- Differentiate between GUI and CLI interaction.
- Recognize different operating system families and their use cases.
- Gather system information using graphical tools.
- Navigate the Linux filesystem to locate information.

---

# Understanding the Operating System

An operating system acts as the bridge between hardware and software.

Instead of applications communicating directly with the CPU, memory, storage, and peripherals, they request services from the operating system. The OS manages these requests, allocates resources, prevents conflicts, and enforces security.

Without an operating system:

- Applications would compete for hardware resources.
- Memory corruption would become common.
- Devices would require application-specific control.
- Security and user management would be nearly impossible.

---

# Kernel Space vs User Space

## Kernel Space

The kernel is the most privileged part of the operating system.

Responsibilities include:

- CPU management
- Memory management
- Device communication
- File system operations
- Process scheduling

The kernel has unrestricted access to hardware.

---

## User Space

Applications run inside User Space.

Programs cannot directly access hardware.

Whenever an application needs to:

- Read a file
- Save data
- Connect to a network
- Play audio
- Access storage

it performs a **system call**, requesting the kernel to perform the operation.

This separation improves stability and security because one faulty application cannot directly damage the operating system.

---

# Core Responsibilities of an Operating System

## Process Management

Responsible for:

- Creating processes
- Scheduling CPU time
- Terminating processes
- Supporting multitasking

Example:

Running a browser, music player, and terminal simultaneously.

---

## Memory Management

Responsible for:

- Allocating RAM
- Protecting process memory
- Reclaiming unused memory
- Using virtual memory when RAM is low

---

## File System Management

Responsible for:

- Organizing files
- Managing directories
- File permissions
- Metadata
- Storage allocation

Example:

Creating folders and saving documents.

---

## User Management

Responsible for:

- User accounts
- Authentication
- Permissions
- Access control

Example:

Each user only accesses files they are authorized to use.

---

## Device Management

Responsible for:

- Loading drivers
- Managing peripherals
- Hardware abstraction

Example:

Automatically detecting a USB flash drive.

---

# Operating System Security

The operating system provides several built-in security mechanisms.

These include:

- Authentication
- Authorization
- Permission management
- Process isolation
- Protection of critical system files

Security begins with the operating system before additional tools such as antivirus software are installed.

---

# GUI vs CLI

## Graphical User Interface (GUI)

Uses:

- Windows
- Icons
- Menus
- Mouse interaction

Advantages:

- Easy to learn
- Visual navigation
- Beginner friendly

---

## Command Line Interface (CLI)

Uses text commands.

Advantages:

- Faster
- More precise
- Scriptable
- Preferred for administration and cybersecurity work

As I continue through TryHackMe, I expect to spend significantly more time working in the CLI.

---

# Types of Operating Systems

| Type | Typical Use |
|-------|-------------|
| Desktop | Personal computing |
| Server | Hosting services and infrastructure |
| Mobile | Smartphones and tablets |
| Embedded | IoT devices, routers, vehicles |
| Virtual / Cloud | Virtual machines and cloud infrastructure |

---

# Common Operating System Families

## Desktop

- Windows
- macOS
- Linux

## Server

- Ubuntu Server
- Debian
- Red Hat
- Windows Server

## Mobile

- Android
- iOS

## Embedded

- OpenWrt
- Ubuntu Core
- FreeRTOS
- QNX

## Cloud

- Ubuntu LTS
- Amazon Linux
- Alpine Linux
- Rocky Linux

---

# Practical Investigation

Using the provided Ubuntu virtual machine, I gathered system information through the graphical interface.

I successfully identified:

- Ubuntu MATE version
- Installed memory
- File system type
- Existing user accounts
- Contents of a user's Documents directory

### Information Retrieved

| Item | Result |
|------|--------|
| Ubuntu Version | 1.26.2 |
| Memory | 1.9 GiB |
| Root Filesystem | ext4 |
| User Directories | 3 |
| Flag | THM{new_pc_for_free!} |

---

# Key Terminology

**Operating System (OS)**

Software responsible for managing hardware and software resources.

**Kernel Space**

Privileged execution environment with unrestricted hardware access.

**User Space**

Environment where applications execute with restricted permissions.

**GUI**

Graphical interface using windows, icons, and menus.

**CLI**

Text-based interface used to interact with the operating system using commands.

**System Call**

A request from an application asking the kernel to perform a privileged operation.

---

# Cybersecurity Relevance

This room established foundational concepts that appear throughout cybersecurity.

Understanding operating systems is critical for:

- Linux administration
- Windows administration
- Privilege escalation
- Malware analysis
- Digital forensics
- Incident response
- Process analysis
- Memory forensics
- File system investigations

Many attack techniques ultimately target operating system components, making this knowledge essential before studying offensive or defensive security.

---

# Key Takeaways

- The operating system coordinates all hardware and software activity.
- The kernel has full hardware privileges while applications operate in User Space.
- Operating systems manage processes, memory, files, users, and hardware.
- GUI simplifies interaction, while CLI provides greater control and efficiency.
- Linux, Windows, macOS, Android, and embedded operating systems are designed for different environments.
- Basic system investigation skills are essential for cybersecurity professionals.

---

# Personal Reflection

This room strengthened my understanding of what an operating system actually does behind the scenes. Before this, I mainly viewed the OS as the interface used to launch applications. I now understand it as the component responsible for coordinating hardware resources, enforcing permissions, and maintaining system stability.

The hands-on investigation also reinforced the importance of collecting system information before making changes to an unfamiliar machine. This mirrors real-world cybersecurity practices where understanding a system is the first step before troubleshooting, hardening, or investigating it.
