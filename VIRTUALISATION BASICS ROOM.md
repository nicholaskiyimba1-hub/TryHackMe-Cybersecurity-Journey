# TryHackMe: Virtualization Basics (Computer Fundamentals Module)

**Room:** Virtualization Basics
**Module:** Computer Fundamentals
**Difficulty:** Beginner
**Write-up by:** Nicholas Kiyimba
**Platform:** TryHackMe

## Why This Room Exists

Before this room, I understood what a computer is made of and how computers talk to each other. This room answered a different question: how do companies run many applications without buying a separate physical computer for every single one?

The old rule was "one server, one application." If a company needed a website, a database, an email system, and an internal app, they bought four separate physical machines. This caused real problems:

* It was expensive. Buying many physical machines costs money, and so does the electricity, cooling, and space they need.
* Most machines were barely used. Many servers only used 5 to 20 percent of their power, so most of what was paid for went to waste.
* Setting up a new physical machine was slow, sometimes taking days or weeks.
* Scaling up meant buying more hardware every time.

Virtualization was built to fix this. The simple idea behind it is: what if many applications could safely share one physical machine instead of each needing its own?

## The Building Analogy (This Is the One I Want to Remember)

Imagine one person living alone in a 10 floor building. They only use one floor, but they still have to pay for and maintain the whole building. Most of it sits empty. That is wasteful.

Now imagine that same building split into separate apartments. Each apartment has its own door, walls, and kitchen, so people can live independently without disturbing each other. But they all still share the building's core structure, like electricity, water, and the elevator. This is cheaper and smarter for everyone.

This maps directly onto virtualization:

* The building is the physical server.
* The apartments are lab machines (VMs).
* The tenants are the applications or operating systems living inside each VM.
* The building manager is the hypervisor, the software that safely divides the building.

## Hypervisor, in Simple Terms

A hypervisor is the software that makes virtualization possible. Think of it as the building manager. Its job is to:

* Split one physical computer into several virtual ones.
* Give each virtual machine its own slice of CPU, memory, and storage.
* Keep every virtual machine isolated, so one cannot interfere with another.
* Control the lifecycle of each VM, meaning it can start, stop, pause, clone, or delete them.

There are two types of hypervisors, and I want to remember the difference clearly because it comes up as an exam-style question:

**Type 1** runs directly on the physical hardware, with no operating system in between. It is fast and efficient, which is why it is used for production servers, database servers, and data centers.

**Type 2** runs on top of an existing operating system, like installing a normal app. It is easier to set up, which makes it the better choice for learning, testing, or small personal setups, like running Kali Linux on my own laptop.

A quick way I remember which to use: if it is serious, always-on, business critical work, think Type 1. If it is for learning, testing, or trying something out, think Type 2.

One important safety point: when testing something malicious, like a suspicious file, I must make sure the host machine cannot get infected by what is running inside the guest VM. This can be done by using a different operating system for the guest than the host, or by isolating the guest so it has no way to communicate with the host.

## Lab Machines (VMs), in Simple Terms

A lab machine, also called a VM, is a virtual computer created by the hypervisor. Even though it is virtual, it behaves like a real computer:

* It has its own virtual CPU, RAM, storage, and network.
* It can run any operating system I choose, such as Windows or Linux.
* It is fully isolated from other VMs, so if one VM crashes or breaks, the others keep working fine.

Tools like Oracle VirtualBox and VMware Workstation let me run VMs on my own computer. These tools are themselves Type 2 hypervisors.

Two real examples of when I would use a VM:

* I want to use Kali Linux but I cannot afford a second computer, so I install a hypervisor and run Kali as a VM instead.
* I want to test if a file is malicious without putting my main computer at risk, so I run it inside an isolated VM instead.

## Containers, in Simple Terms

A container is a lighter, smaller version of the same idea. Instead of packing a whole separate operating system like a VM does, a container shares the kernel of the host system. The kernel is the core part of an operating system that talks to the hardware and manages resources like memory and running programs.

Because containers share the host's kernel instead of bringing their own OS, they:

* Start almost instantly, since there is no full OS to boot.
* Use fewer resources than a VM.
* Stay isolated from each other, so one broken container does not affect the others.
* Run consistently across different machines, which makes them great for development, testing, and deployment.

The catch is that because containers share the host's kernel, they must match the host's OS type. I cannot run a Windows container on a Linux machine.

Docker is the easiest tool to create and manage containers. It is an open source platform built specifically for this kind of containerization work.

## VM vs Container, the Short Version

I keep this comparison simple in my head: a VM is like a full apartment, complete and separate, with maximum isolation and flexibility. A container is like a small room inside that apartment, lightweight and fast, built for quick and scalable deployment.

## Hands On Practice: AutoGalo Scenario

The room put me in the role of the person responsible for virtualization at a company called AutoGalo, using a tool called Virtualization Manager. This tool gave me a clear view of the whole environment, including every VM and every physical host.

**Investigating the email issue:** Everyone at the company stopped receiving emails. I found the VM named `Mail-SERVER` sitting in an Error state inside the Lab Machines section, and restarted it. After the restart, it went back to working normally.

**Creating a new VM:** I created a VM for the marketing team's website with these specs:
* Name: `Marketing-VM`
* CPU Cores: 4
* Memory: 8 GB
* Disk Size: 100 GB

**Checking host health:** In the Hosts section, I reviewed the physical machines behind all the VMs and found:
* `HV-PROD-01` still had room for more VMs.
* `HV-PROD-02` was almost at full capacity, which is something worth reporting to a manager before it becomes a problem.
* `HV-BACKUP-01` was disconnected and was not hosting anything.

This part of the room felt the most useful for real exam prep, since it forced me to actually read and interpret a virtualization dashboard instead of just memorizing definitions.

## Key Terms 

* **Virtualization:** Lets one physical computer act like several separate computers.
* **Hypervisor:** The manager software that creates and controls virtual machines.
* **Lab Machine (VM):** A complete virtual computer with its own operating system.
* **Container:** A small, isolated space for a single app that shares the host's operating system.
* **Container Image:** A ready made template used to create a container.
* **Network Ports:** The numbered entry points apps use to communicate over a network.

## Benefits of Virtualization 

* Cost savings
* Better resource usage
* Safer testing for cybersecurity work
* Faster deployment
* Flexibility
* Portability
* Scalability
* Centralized management

## Why This Matters To Me

This room gave me the reasoning behind something I already use, since I run Kali Linux as a VM myself. Understanding hypervisors, VMs, and containers properly is also going to matter directly for cloud computing, since cloud services are built on exactly these same ideas.

---
*This write-up documents my own progress through TryHackMe as I work through the Computer Fundamentals module, written in simple language for my own future review and certification exam preparation.*
