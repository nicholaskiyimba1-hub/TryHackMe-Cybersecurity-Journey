# Windows Basics

**Platform:** TryHackMe  
**Module:** Operating System Basics  
**Room:** Windows Basics  
**Status:** ✅ Completed

---

# Objective

This room introduced the Windows operating system from a practical perspective. I learned how to navigate the Windows graphical interface, manage files, view system information, install applications, use built-in administration tools, and explore native Windows security features.

The practical lab simulated my first day as an employee at TryHatMe, where I completed onboarding tasks using a Windows Server 2019 workstation.

---

# Learning Outcomes

After completing this room, I can:

- Navigate the Windows desktop confidently.
- Use the Start Menu, Taskbar, and Search efficiently.
- Manage files and folders using File Explorer.
- Locate system information through Windows Settings.
- Install and uninstall Windows applications.
- Monitor system performance with Task Manager.
- Use Windows Security to perform malware scans.
- Understand the purpose of Windows Defender Firewall.
- Differentiate between administrator and standard user permissions.

---

# Introduction to Windows

Microsoft Windows is the world's most widely used desktop operating system.

Modern versions of Windows provide:

- A graphical user interface (GUI)
- Built-in security features
- User account management
- Hardware management
- File management
- Application management

Unlike early versions that relied heavily on MS-DOS commands, modern Windows allows users to interact primarily through graphical components such as windows, icons, menus, and buttons.

---

# User Authentication

Before accessing Windows, users must authenticate.

Windows supports different account types.

## Guest Account

- Temporary access
- Very limited permissions
- Cannot modify system settings

## Standard User

- Daily computing tasks
- Can run applications
- Cannot perform system-wide administrative changes

## Administrator

- Full control of the operating system
- Install software
- Manage users
- Change system settings
- Access protected resources

During this room, I worked with an **Administrator** account.

---

# Windows Desktop

The Windows Desktop is the primary workspace after logging into the system.

Its main components include:

- Desktop icons
- Taskbar
- Start Menu
- Search
- Task View
- Notification area
- Date and Time
- Network and Audio controls

These components provide quick access to applications, settings, and system functions.

---

# Start Menu

The Start Menu acts as the central navigation point in Windows.

Using it, I can:

- Launch applications
- Open Settings
- Search files
- Search applications
- Access power options
- Sign out or restart the computer

---

# File Explorer

File Explorer is Windows' built-in file management tool.

It allows users to:

- Browse folders
- Create directories
- Copy files
- Move files
- Rename files
- Delete files
- Search for files

Windows organizes files using a hierarchical folder structure.

Example:

```
C:\Users\Administrator\Desktop\TryHatMe Onboarding
```

Understanding file paths is essential for Windows administration and cybersecurity investigations.

---

# System Information

Using **About your PC**, I collected important information about the workstation.

### Information Gathered

| Item | Result |
|------|--------|
| Device Name | TryHatMe |
| Installed RAM | 4.00 GB |
| Windows Version | 1809 |
| Welcome Flag | THM{welcome_to_tryhatme!} |

---

# Application Management

Windows applications can be managed through:

- Microsoft Store
- Vendor installers (.exe / .msi)
- Windows Settings
- Control Panel

Keeping applications updated is important because updates frequently include:

- Security patches
- Bug fixes
- Performance improvements

---

# Installing Applications

As part of the onboarding exercise, I installed the provided application.

### Result

Successfully installed:

- TryHatMeWelcome

Flag obtained:

```
THM{your_first_day!}
```

This exercise demonstrated the standard Windows software installation process using an executable installer.

---

# Windows Settings

Windows Settings provides centralized configuration for:

- Devices
- Personalization
- Accounts
- Time & Language
- Network
- Privacy
- Security
- Applications

Information discovered:

| Setting | Value |
|---------|-------|
| Region | United States |

---

# Control Panel

Although Windows Settings is the modern configuration interface, many advanced administrative options remain inside the Control Panel.

One exercise required changing the Control Panel view to **Small icons**, making every available configuration tool visible in a single window.

This reinforced the importance of carefully reading task instructions rather than making assumptions about the required action.

---

# Task Manager

Task Manager provides real-time information about system activity.

Important tabs include:

## Processes

Displays running applications and background processes.

## Performance

Shows resource utilization including:

- CPU
- Memory
- Disk
- Network

## Users

Displays currently logged-in users.

Result:

| Item | Value |
|------|-------|
| Logged-in User | Administrator |

## Details

Provides process IDs (PIDs) and technical process information.

## Services

Displays Windows services and their current status.

Task Manager is an essential troubleshooting and incident response tool.

---

# Windows Security

Windows includes built-in security features without requiring third-party software.

Key protection areas include:

- Virus & Threat Protection
- Firewall & Network Protection
- App & Browser Control
- Device Security

I performed a custom malware scan on the onboarding folder.

Detected test file:

```
tryhatmemaldoc.txt
```

This demonstrated how Windows Defender detects known malware signatures such as the EICAR test file.

---

# Windows Defender Firewall

Windows Defender Firewall controls network traffic entering and leaving the computer.

Network profiles include:

- Domain
- Private
- Public

The firewall allows administrators to:

- Create inbound rules
- Create outbound rules
- Allow applications
- Block applications
- Monitor network connections

Firewall configuration is an important component of endpoint security.

---

# Practical Investigation

During the lab I completed the following tasks:

- Investigated system specifications.
- Explored Windows Settings.
- Navigated the Windows desktop.
- Used File Explorer.
- Located onboarding documentation.
- Installed an application.
- Changed Control Panel view.
- Explored Task Manager.
- Performed a Windows Defender custom scan.
- Investigated detected files.
- Reviewed built-in Windows security tools.

---

# Key Terminology

**Desktop**

Primary Windows workspace.

**Taskbar**

Quick-access bar containing applications, notifications, and system controls.

**Start Menu**

Central navigation interface for launching applications and accessing settings.

**File Explorer**

Windows file management application.

**Windows Settings**

Modern system configuration interface.

**Control Panel**

Legacy administrative interface that still contains many advanced configuration tools.

**Task Manager**

Tool used to monitor processes, performance, services, and logged-in users.

**Windows Security**

Central dashboard for Windows' built-in security protections.

**Windows Defender Firewall**

Built-in firewall responsible for filtering network traffic.

---

# Cybersecurity Relevance

Windows dominates enterprise environments, making Windows administration an essential cybersecurity skill.

The concepts introduced in this room are foundational for:

- Windows system administration
- Digital forensics
- Incident response
- Malware analysis
- Active Directory environments
- Endpoint security
- Security auditing
- Privilege management

Understanding how Windows organizes files, users, processes, and security controls is critical before moving into more advanced security topics.

---

# Challenges Encountered

One task required changing the Control Panel to **Small icons** view.

Initially, I misunderstood the instruction and assumed it referred to changing the size of desktop icons rather than the Control Panel display mode. After carefully rereading the task, I located the **View by** dropdown inside the Control Panel and completed the exercise successfully.

This reminded me that accurate interpretation of instructions is just as important as technical knowledge, especially in cybersecurity where overlooking small details can lead to incorrect conclusions.

---

# Key Takeaways

- Windows uses graphical tools to simplify system administration.
- File Explorer is central to Windows file management.
- Administrator accounts provide elevated privileges.
- Task Manager is invaluable for monitoring processes and system performance.
- Windows Security provides built-in endpoint protection.
- Windows Defender Firewall controls inbound and outbound network traffic.
- Careful reading of technical instructions prevents unnecessary troubleshooting.

---

# Personal Reflection

This room transformed my understanding of Windows from simply being an operating system I use daily into a platform with structured administration, security, and management tools. Before this room, I mainly interacted with Windows as an end user. I now have a much clearer understanding of where to find system information, how Windows organizes files and settings, how applications are managed, and how built-in security features help protect the system.

One lesson that stood out was the importance of reading technical instructions carefully. I realized I sometimes jump to conclusions before fully understanding a task. Correcting that habit will improve both my troubleshooting skills and my effectiveness during future cybersecurity labs and real-world investigations.
