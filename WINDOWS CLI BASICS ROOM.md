# Windows CLI Basics

> **Room:** Windows CLI Basics  
> **Platform:** TryHackMe  
> **Module:** Operating System Basics  
> **Difficulty:** Beginner  

---

## Overview

The **Windows CLI Basics** room introduced me to using the **Windows Command Prompt (CMD)** to perform administrative tasks without relying on the graphical interface. Since Windows is the dominant desktop operating system in enterprise environments, becoming comfortable with the command line is an essential skill for IT support, system administration, digital forensics, incident response, and cybersecurity.

Throughout the room, I completed practical tasks as a new cybersecurity intern. Rather than simply memorizing commands, I learned how each command is used to investigate a Windows system, locate files, and collect system information—skills that mirror real-world IT and security workflows.

---

# Learning Objectives

By completing this room, I learned how to:

- Navigate the Windows filesystem using Command Prompt.
- Move between directories without using File Explorer.
- Search for files recursively.
- Display file contents directly in the terminal.
- Gather important system information.
- Retrieve basic network information.
- Build confidence using the Windows command-line interface.

---

# Why the Windows Command Line Matters

Although Windows provides a graphical interface for most daily tasks, cybersecurity professionals frequently rely on the Command Prompt because it offers:

- Faster navigation.
- Greater precision.
- Easier automation.
- Better troubleshooting capabilities.
- Access to information that may not be immediately visible in the GUI.
- Compatibility with many administrative and security tools.

Being comfortable with the Windows CLI is an important step toward becoming an effective cybersecurity professional.

---

# Practical Walkthrough

## 1. Determining the Current Directory

The first command I used was:

```cmd
cd
```

Unlike Linux, where `pwd` displays the current working directory, Windows uses `cd` without any arguments to display the current location.

This helps confirm where I am before navigating elsewhere.

---

## 2. Listing Directory Contents

To display files and folders in the current directory, I used:

```cmd
dir
```

The command displays:

- Files
- Directories
- File sizes
- Creation dates
- Available storage

This is the Windows equivalent of Linux's `ls` command.

---

## 3. Viewing Hidden Files

Some files and folders are hidden by default.

To reveal them, I used:

```cmd
dir /a
```

The `/a` switch displays all files, including hidden and system files.

This command is particularly useful during system administration, troubleshooting, and digital forensics, where important files may not appear during a normal directory listing.

---

## 4. Navigating Between Directories

To move into another directory, I used:

```cmd
cd FolderName
```

Example:

```cmd
cd Documents
```

To move back one directory:

```cmd
cd ..
```

Understanding directory navigation is fundamental because nearly every administrative task begins with locating the correct folder.

---

## 5. Searching for Files

Instead of manually searching through folders, I used:

```cmd
dir /s task_brief.txt
```

The `/s` option performs a recursive search through all subdirectories.

This located the file at:

```text
C:\Users\Administrator\Documents\Notes\research_yn6\exports_imv\screenshots\notes_wi6
```

Recursive searching is far more efficient than manually browsing large directory structures.

---

## 6. Reading File Contents

To display the contents of the discovered file, I used:

```cmd
type task_brief.txt
```

Unlike opening Notepad, the `type` command prints the contents directly inside Command Prompt.

This is useful when reviewing:

- Log files
- Configuration files
- Text documents
- Evidence during investigations

---

# Gathering System Information

One of the first tasks when investigating a Windows system is identifying the environment.

---

## Current Logged-in User

Command:

```cmd
whoami
```

Output:

```text
Administrator
```

This identifies the account currently logged into the system.

Knowing the active user helps determine available privileges.

---

## Computer Name

Command:

```cmd
hostname
```

Output:

```text
thmlab
```

Every Windows computer has a hostname used for identification on a network.

Hostnames are commonly referenced during:

- Asset management
- Network administration
- Incident response
- Digital investigations

---

## Operating System Information

Command:

```cmd
systeminfo
```

This command displays detailed information about the operating system, including:

- Windows edition
- Build number
- System architecture
- Processor
- Installed memory
- Boot time

During the lab I identified:

**Windows Version**

```text
10.0.17763 N/A Build 17763
```

Gathering system information is one of the first steps in troubleshooting or investigating a machine.

---

## Network Configuration

Command:

```cmd
ipconfig
```

This displays:

- IPv4 Address
- Subnet Mask
- Default Gateway
- Network adapters

Understanding network configuration is essential for diagnosing connectivity problems and performing network investigations.

---

# Practical Investigation

During this lab I successfully:

- Located a hidden task file.
- Read its contents using the terminal.
- Navigated Windows directories entirely through Command Prompt.
- Identified the logged-in user.
- Determined the computer hostname.
- Retrieved Windows version information.
- Inspected network configuration.

The room demonstrated how common Windows command-line utilities support day-to-day IT operations and cybersecurity investigations.

---

# Commands Learned

| Command | Purpose |
|----------|---------|
| `cd` | Display or change the current directory |
| `dir` | List files and folders |
| `dir /a` | Show hidden files and folders |
| `dir /s filename` | Search recursively for a file |
| `type filename` | Display file contents |
| `whoami` | Display the current logged-in user |
| `hostname` | Display the computer name |
| `systeminfo` | Display detailed system information |
| `ipconfig` | Display network configuration |

---

# Key Concepts

- Windows Command Prompt provides a text-based interface for interacting with the operating system.
- Hidden files can be displayed using `dir /a`.
- Recursive file searches simplify locating files in large directory structures.
- System information should always be gathered before troubleshooting or investigating a machine.
- Network configuration provides insight into how a computer communicates with other systems.
- Many enterprise administration and cybersecurity tasks rely heavily on command-line tools.

---

# Skills Gained

After completing this room, I can confidently:

- Navigate the Windows filesystem using CMD.
- Search for files efficiently.
- Read files directly from the terminal.
- Identify the current user.
- Determine a computer's hostname.
- Gather operating system information.
- Inspect network configuration.
- Use Windows CLI to perform basic system investigations.

These skills establish a strong foundation for more advanced Windows administration, digital forensics, incident response, malware analysis, and penetration testing.

---

# Key Takeaways

- The Windows Command Prompt is a powerful administrative tool.
- CLI skills improve efficiency compared to relying solely on graphical interfaces.
- Basic investigation begins with gathering information about users, the operating system, and the network.
- Understanding both Linux and Windows command-line environments is essential for cybersecurity professionals, as enterprise environments commonly use both operating systems.

---

## Room Status

**Room Completed Successfully** ✅

### Flags Obtained

- **TASK-BRIEF-FOUND**

---

*This write-up documents my understanding after completing the **Windows CLI Basics** room on TryHackMe. It serves as both a revision resource for future certification preparation and a record of my practical cybersecurity learning journey.*
