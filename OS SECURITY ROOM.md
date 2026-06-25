# OS Security - TryHackMe Writeup

## Overview

This room introduced fundamental Operating System Security concepts through hands-on interaction with a Linux target machine. The exercises focused on authentication, file system navigation, user account management, privilege escalation, and accessing protected resources.

---

## Learning Objectives

* Understand Linux file system structure
* Navigate directories using the command line
* Discover hidden files and directories
* Authenticate to remote systems using SSH
* Switch between user accounts
* Identify privilege escalation opportunities
* Access protected resources as the root user

---

## Skills Practiced

### Linux Navigation

Commands used:

```bash
pwd
ls
ls -la
cd
find
cat
```

Key concepts learned:

* The root directory (`/`) is the top of the Linux file system.
* Hidden files and directories begin with a dot (`.`).
* `pwd` displays the current working directory.
* `find` can be used to locate files throughout the system.

---

### SSH Authentication

Successfully connected to the target system using discovered credentials.

Example:

```bash
ssh username@target-ip
```

This established the initial foothold required for further enumeration.

---

### Enumeration

After gaining access, the system was explored to identify:

* Users
* Directories
* Hidden files
* Potential credential sources

Enumeration proved to be one of the most important phases of the exercise.

---

### User Switching

The `su` command was used to switch between user accounts.

Example:

```bash
su username
```

This demonstrated how access to additional accounts can lead to higher privileges.

---

### Privilege Escalation

The objective of privilege escalation is to obtain administrative access.

Verification command:

```bash
whoami
```

Expected result:

```text
root
```

Obtaining root privileges provided unrestricted access to the operating system.

---

### Flag Retrieval

After escalating privileges, navigation to the root user's directory was performed.

Commands used:

```bash
cd /root
ls -la
cat flag.txt
```

Successfully reading the flag confirmed full system compromise and completion of the room objectives.

---

## Key Lessons Learned

### 1. Enumeration Is Critical

Many security assessments are won through careful enumeration rather than exploitation.

Always inspect:

* User directories
* Hidden files
* Configuration files
* Command history

---

### 2. Hidden Files Matter

Display hidden files using:

```bash
ls -la
```

Important information is often stored in hidden files such as:

```text
.bash_history
.profile
.ssh
```

---

### 3. Be Systematic

Avoid randomly guessing passwords.

Instead:

1. Gather information.
2. Search for credentials.
3. Check shell history.
4. Review configuration files.
5. Test likely passwords methodically.

---

### 4. Verify Privileges

Always confirm privilege level before attempting privileged actions.

```bash
whoami
```

This avoids confusion and validates successful privilege escalation.

---

## Commands Learned

```bash
pwd
ls
ls -la
cd
find
cat
ssh
su
whoami
```

---

## Takeaway

This room provided practical experience with Linux system navigation, SSH access, enumeration, privilege escalation, and root-level access. The most important lesson was that careful enumeration often reveals the information needed to achieve higher privileges and complete security objectives.
