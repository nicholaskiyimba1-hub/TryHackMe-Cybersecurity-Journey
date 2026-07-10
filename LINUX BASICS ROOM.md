# Linux CLI Basics

> **Room:** Linux CLI Basics  
> **Platform:** TryHackMe  
> **Module:** Operating System Basics  
> **Status:** ✅ Completed

---

# Overview

This room introduced me to the Linux Command-Line Interface (CLI), the primary way Linux systems are managed in cybersecurity. Instead of relying on a graphical interface, I learned how to interact directly with the operating system using commands to navigate the filesystem, locate files, inspect system information, and read configuration files.

The room was presented as a real-world onboarding scenario where I joined a Cyber Operations Support Team as a new IT Support Engineer. Through practical missions, I completed tasks that closely resemble the daily responsibilities of Linux system administrators and cybersecurity professionals.

---

# Learning Objectives

After completing this room, I can:

- Explain what the Linux Command-Line Interface (CLI) is.
- Navigate the Linux filesystem using terminal commands.
- Locate files using search commands.
- Display the contents of files.
- Retrieve system information from Linux.
- Read important operating system configuration files.
- Apply multiple Linux commands together to solve practical tasks.

---

# Key Concepts Learned

## What is the Linux CLI?

The Command-Line Interface (CLI) is a text-based method of interacting with Linux.

Unlike a GUI where actions are performed using icons and menus, the CLI allows users to issue precise commands directly to the operating system.

In cybersecurity, the terminal is preferred because it:

- Provides greater control over the operating system.
- Executes tasks faster than navigating through graphical menus.
- Allows automation through scripts.
- Supports numerous security and forensic tools that have no graphical interface.

---

## Navigating the Linux Filesystem

The filesystem is organized as a hierarchy beginning at the root directory (`/`).

I learned how to determine my current location, move between directories, list directory contents, and return to parent directories.

### Commands Practiced

| Command | Purpose |
|----------|---------|
| `pwd` | Display current working directory |
| `ls` | List files and directories |
| `ls -l` | Long listing format |
| `ls -al` | Display all files, including hidden files |
| `cd directory` | Move into a directory |
| `cd ..` | Move one directory upward |

---

## Hidden Files

Linux hides files that begin with a period (`.`).

These are typically configuration files rather than secret files.

To display hidden files:

```bash
ls -al
```

---

## Searching for Files

Instead of manually browsing the filesystem, Linux provides the powerful `find` command.

### Syntax

```bash
find <starting_directory> -name <filename>
```

Example:

```bash
find ~ -name mission_brief.txt
```

This recursively searches every directory beneath the specified starting location.

---

## Reading Files

Once a file is located, the `cat` command displays its contents.

Example:

```bash
cat mission_brief.txt
```

This command is frequently used to read:

- Configuration files
- Log files
- Documentation
- Flags during CTF challenges

---

# Collecting System Information

A significant part of system administration involves identifying the environment you're working in.

I learned several commands used by Linux administrators every day.

---

## Determine Current User

```bash
whoami
```

Returns the currently authenticated username.

Example:

```text
ubuntu
```

---

## Display Kernel Information

```bash
uname -a
```

Provides:

- Operating system
- Hostname
- Kernel version
- Architecture

Example output includes:

- Linux
- Hostname
- Kernel Version
- x86_64 Architecture

---

## Check Disk Usage

```bash
df -h
```

The `-h` option displays sizes in human-readable units.

Information includes:

- Total disk size
- Used storage
- Available storage
- Percentage used

---

## Reading Operating System Information

Linux distributions maintain operating system information inside:

```text
/etc/os-release
```

Reading the file:

```bash
cat /etc/os-release
```

Provides details such as:

- Distribution Name
- Version
- Codename
- Vendor
- Support URLs

Example:

```text
Ubuntu 24.04.1 LTS
```

---

# Practical Exercises Completed

## Mission 1

Successfully located:

```
mission_brief.txt
```

using:

```bash
find
```

Navigated to the directory using:

```bash
cd
```

Displayed the file contents using:

```bash
cat
```

Retrieved the challenge flag:

```
MISSION-FOUND
```

---

## Mission 2

Collected system information including:

- Current user
- Kernel version
- Available disk space
- Linux distribution

using:

```bash
whoami
uname -a
df -h
cat /etc/os-release
```

---

## Mini Challenge

Independently completed the final exercise by:

- Finding `day1_report.txt`
- Navigating to its directory
- Reading its contents

Successfully recovered:

```
END-OF-DAY1
```

without guided instructions.

---

# Commands Learned

| Command | Description |
|----------|-------------|
| `pwd` | Print working directory |
| `ls` | List directory contents |
| `ls -l` | Detailed directory listing |
| `ls -al` | Show hidden files |
| `cd` | Change directory |
| `cd ..` | Move to parent directory |
| `find` | Search for files |
| `cat` | Display file contents |
| `whoami` | Display current user |
| `uname -a` | Display kernel and system information |
| `df -h` | Display disk usage |
| `cat /etc/os-release` | Display Linux distribution information |

---

# Key Takeaways

- Linux administration relies heavily on the command line.
- Knowing where I am in the filesystem is essential before performing operations.
- Hidden files usually contain configuration rather than sensitive information.
- The `find` command is far more efficient than manually searching directories.
- Many important Linux configuration files are stored under `/etc`.
- System identification is one of the first tasks performed during security assessments, troubleshooting, or incident response.

---

# Skills Developed

- Linux filesystem navigation
- Terminal usage
- File searching
- Reading configuration files
- Basic Linux system enumeration
- Interpreting system information
- Using multiple commands together to complete practical tasks

---

# Mission Debrief

## WIN

Successfully navigated the Linux filesystem entirely through the command line, locating files, reading their contents, and gathering important system information using standard Linux administration commands.

Understanding foundational CLI commands builds the confidence and efficiency required for Linux administration, cybersecurity operations, and penetration testing.

### Flow

- Determined current working directory
- Listed directory contents
- Navigated through the filesystem
- Located files using `find`
- Read files with `cat`
- Enumerated system information
- Completed the independent end-of-day challenge

---

## IMPROVEMENT

Although I successfully completed every task, I occasionally paused to remember command syntax. Increasing repetition will make commonly used Linux commands feel automatic during future labs and real-world work.

Strong command recall improves speed, reduces mistakes, and allows greater focus on solving security problems instead of remembering syntax.

### Flow

- Occasionally verified command structure before execution
- Relied on room examples for a few commands
- Successfully completed all tasks after applying the correct syntax

---

# ACTION POINTS

- Practice Linux CLI daily until commands become second nature, especially `pwd`, `ls`, `cd`, `find`, `cat`, `whoami`, `uname`, and `df`.

- Continue exploring the Linux filesystem beyond the room by examining directories such as `/etc`, `/var`, `/home`, `/usr`, and `/tmp` to build familiarity with the operating system's structure.

- Begin developing the habit of chaining multiple commands together during investigations, as this forms the foundation for Linux administration, digital forensics, penetration testing, and incident response.

---

# Overall Reflection

This room marked my first serious hands-on experience using Linux exclusively through the command line. Rather than memorizing commands in isolation, I applied them to realistic tasks such as locating files, gathering system information, and investigating a Linux system as a new IT Support Engineer.

These skills form the foundation for nearly every cybersecurity discipline—including penetration testing, digital forensics, SOC analysis, cloud security, and Linux server administration. Mastering these basics will make it much easier to learn advanced Linux concepts in future TryHackMe rooms and prepare for professional cybersecurity certifications.
