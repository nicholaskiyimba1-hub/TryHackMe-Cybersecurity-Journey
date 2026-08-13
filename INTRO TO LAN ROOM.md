# Intro to LAN Room

## Introduction

This room introduced me to how **Local Area Networks (LANs)** are designed and how devices communicate within them.

The main topics I covered were:

- LAN topologies
- Switches and routers
- Subnetting
- ARP
- DHCP

I found this room useful because it moved beyond simply understanding that devices are connected and started explaining **how those devices are organised and communicate with each other**.

---

# Task 1: Introduction to LAN Topologies

## What is a LAN?

LAN stands for **Local Area Network**.

A LAN is a network that connects devices within a relatively limited area, such as:

- A home
- School
- Office
- Business
- Building

One of the first things I learned in this task was the concept of a **network topology**.

A topology is basically the way devices are arranged and connected within a network.

The three topologies covered were:

1. Star
2. Bus
3. Ring

---

## Star Topology

In a **star topology**, devices are individually connected to a central networking device, usually a switch.

I visualised it like this:

```text
              PC
               |
               |
PC -------- SWITCH -------- PC
               |
               |
            Printer
```

The central device acts as the point through which the connected devices communicate.

### Advantages

One major advantage of a star topology is **scalability**.

It is relatively easy to add another device to the network by connecting it to the central switch.

It is also more reliable than some older topologies because the failure of one cable normally only affects the device connected to that cable.

### Disadvantages

The main disadvantages I noted were:

- More cabling is required
- A switch or other central device is required
- It can be more expensive
- The central device becomes a potential single point of failure

If the central switch fails, the devices connected through it can no longer communicate through that network.

---

## Bus Topology

A **bus topology** uses a single main cable, called the **backbone**, with devices connected along it.

```text
PC      PC       PC       PC
 |       |        |        |
================================
          Backbone
```

One advantage is that it is relatively cheap and simple to set up because it doesn't require a dedicated central device like a star topology.

However, I learned that this design has some serious disadvantages.

Since all devices share the same backbone, a lot of traffic can cause congestion and create a **bottleneck**.

Troubleshooting can also be difficult because many devices are using the same connection.

Another major problem is the lack of redundancy. If the backbone cable fails, the network can be disrupted.

---

## Ring Topology

In a **ring topology**, devices are connected directly to one another in a loop.

```text
       PC -------- PC
       |            |
       |            |
       PC -------- PC
```

Data travels around the ring until it reaches the intended device.

One interesting thing I learned is that devices can forward data received from another device, but if they have their own data to send, they send their own data first.

### Advantages

- Requires less cabling than a star topology
- Doesn't require as much dedicated networking hardware
- Can have fewer bottlenecks than a bus topology
- Faults can sometimes be easier to trace

### Disadvantages

The major weakness is that a failure in the ring can affect the entire network.

For example, if a device or cable in the ring breaks, communication around the network can be interrupted.

---

# Switches

A **switch** is a networking device used to connect multiple devices on a LAN.

Devices such as computers and printers can connect to the switch using Ethernet cables.

Switches are commonly found in places such as:

- Businesses
- Schools
- Offices
- Larger networks

Switches can have different numbers of ports, such as:

```text
4
8
16
24
32
64
```

## Why switches are better than hubs

A switch keeps track of which devices are connected to which ports.

When it receives a packet, it can forward that packet toward the intended device rather than simply sending it to every connected port.

This reduces unnecessary network traffic.

---

# Routers

A **router** connects different networks and allows data to travel between them.

The process of moving data between networks is called **routing**.

I found it useful to separate the two concepts:

```text
Switch → connects devices within a network

Router → connects different networks
```

Routers determine paths that data can take between networks.

The verb associated with the job performed by routers is:

**Routing**

---

# Network Redundancy

Another concept introduced here was **redundancy**.

Multiple switches and routers can be connected using different paths.

For example:

```text
Network A
    |
   R1
  /  \
 R2  R3
  \  /
   R4
    |
Network B
```

If one path fails, another path can potentially still carry the traffic.

This increases reliability because the network doesn't necessarily depend on a single path.

---

# Practical: Breaking LAN Topologies

The task included an interactive lab where I had to interact with different LAN topologies and identify how they could fail.

The practical helped me understand the weaknesses of the different designs rather than just memorising their advantages and disadvantages.

The key idea was that **network topology affects reliability, scalability, cost, and troubleshooting**.

### Task Answers

**What does LAN stand for?**

`Local Area Network`

**What is the verb given to the job that routers perform?**

`Routing`

**What device is used to centrally connect multiple devices on the local network and transmit data to the correct location?**

`Switch`

**What topology is cost-efficient to set up?**

`Bus`

**What topology is expensive to set up and maintain?**

`Star`

**Flag from the interactive LAN topology lab:**

`[Flag obtained from the completed practical]`

---

# Task 2: A Primer on Subnetting

## What is Subnetting?

Subnetting means dividing a larger network into smaller networks called **subnets**.

I think of it as splitting one large network into smaller sections so that devices can be organised more efficiently.

For example, a business might have different departments such as:

```text
Company Network
│
├── Accounting
├── Finance
└── Human Resources
```

Instead of putting everything into one large network, subnetting can be used to separate these groups.

---

# Subnet Masks

A subnet mask helps determine which part of an IP address represents the network and which part represents the host.

Like an IPv4 address, a subnet mask contains **32 bits** and is represented using four octets.

Each octet has a range of:

```text
0 – 255
```

For example:

```text
255.255.255.0
```

---

# Three Important Addresses

The room introduced three important concepts associated with subnetting.

## Network Address

The **network address** identifies the network itself.

For example:

```text
192.168.1.0
```

can represent the network containing addresses such as:

```text
192.168.1.1
192.168.1.2
192.168.1.100
```

## Host Address

A host address identifies an individual device within the network.

For example:

```text
192.168.1.100
```

could identify a particular computer on the network.

## Default Gateway

The **default gateway** is the device responsible for forwarding traffic to another network.

For example:

```text
192.168.1.254
```

could be used as the gateway.

A simple way I remember this is:

```text
Network Address → identifies the network

Host Address → identifies a device

Default Gateway → provides a path to another network
```

---

# Why Subnetting Matters

Subnetting has several benefits:

- Efficiency
- Security
- Control

The security aspect was particularly interesting to me.

For example, a café could separate its network into:

```text
Employee Network
       |
       |---- Staff computers
       |---- Cash registers
       |---- Internal devices


Guest Network
       |
       |---- Customer devices
       |---- Guest Wi-Fi
```

This separation reduces the need for guest devices to be directly connected to sensitive internal systems.

### Task Answers

**What is the technical term for dividing a network into smaller pieces?**

`Subnetting`

**How many bits are in a subnet mask?**

`32`

**What is the range of a section (octet) of a subnet mask?**

`0–255`

**What address is used to identify the start of a network?**

`Network address`

**What address is used to identify devices within a network?**

`Host address`

**What is the name used to identify the device responsible for sending data to another network?**

`Default gateway`

---

# Task 3: ARP

## What is ARP?

ARP stands for:

**Address Resolution Protocol**

I learned that ARP is used to associate an **IP address** with a **MAC address** on a local network.

This is important because devices use IP addresses as logical identifiers, while MAC addresses are used as physical identifiers associated with network interfaces.

A device therefore needs to discover the MAC address associated with an IP address before it can communicate with that device on the local network.

---

# ARP Request

An **ARP Request** is broadcast across the local network.

The basic question being asked is essentially:

```text
Who has this IP address?
```

For example:

```text
Who has 192.168.1.10?
```

The device that owns that IP address responds.

---

# ARP Reply

The device that owns the requested IP address sends an **ARP Reply** containing its MAC address.

The requesting device can then store the mapping in its **ARP cache**.

The process can be simplified as:

```text
Device A
   |
   | ARP Request
   | "Who has 192.168.1.10?"
   ↓
Local Network
   |
   ↓
Device B
   |
   | ARP Reply
   | "192.168.1.10 is at AA:BB:CC:DD:EE:FF"
   ↓
Device A
```

The important relationship is:

```text
IP Address → MAC Address
```

### Task Answers

**What does ARP stand for?**

`Address Resolution Protocol`

**What category of ARP packet asks a device whether it has a specific IP address?**

`ARP Request`

**What address is used as a physical identifier for a device on a network?**

`MAC address`

**What address is used as a logical identifier for a device on a network?**

`IP address`

---

# Task 4: DHCP

## What is DHCP?

DHCP stands for:

**Dynamic Host Configuration Protocol**

DHCP is used to automatically assign IP configuration to devices joining a network.

Without DHCP, IP addresses could be configured manually on individual devices.

With DHCP, a device can request an IP address from a DHCP server.

---

# DHCP Process

The room introduced four main DHCP messages.

I found the sequence useful to remember as:

```text
Discover → Offer → Request → ACK
```

Or:

```text
DORA
```

---

## 1. DHCP Discover

When a device joins a network and needs an IP address, it sends a **DHCP Discover** packet.

It is essentially asking:

> Is there a DHCP server that can give me an IP address?

---

## 2. DHCP Offer

The DHCP server responds with a **DHCP Offer**.

The offer contains an IP address that the client can use.

---

## 3. DHCP Request

The client then sends a **DHCP Request** to indicate that it wants to use the offered IP address.

---

## 4. DHCP ACK

Finally, the DHCP server sends a **DHCP ACK** (acknowledgement).

This confirms that the client can use the assigned IP configuration.

The complete process is:

```text
Client                    DHCP Server
  |                            |
  |---- DHCP Discover -------->|
  |                            |
  |<----- DHCP Offer ----------|
  |                            |
  |---- DHCP Request --------->|
  |                            |
  |<------- DHCP ACK ----------|
  |                            |
```

### Task Answers

**What type of DHCP packet is used by a device to retrieve an IP address?**

`DHCP Discover`

**What type of DHCP packet does a device send once it has been offered an IP address?**

`DHCP Request`

**What is the last DHCP packet sent to a device from a DHCP server?**

`DHCP ACK`

---

# Key Things I Learned

| Topic | What I learned |
|---|---|
| LAN | Local Area Network |
| Topology | The design/arrangement of a network |
| Star | Devices connect to a central device |
| Bus | Devices share a backbone cable |
| Ring | Devices form a loop |
| Switch | Connects devices within a LAN and forwards traffic appropriately |
| Router | Connects different networks |
| Routing | Process of moving data between networks |
| Subnetting | Dividing a network into smaller networks |
| Subnet mask | 32-bit value used to define network/host portions |
| Network address | Identifies the network |
| Host address | Identifies a device |
| Default gateway | Device used to reach other networks |
| ARP | Maps IP addresses to MAC addresses |
| DHCP | Automatically provides IP configuration |
| DORA | Discover, Offer, Request, ACK |

---

# Important Things I Took From This Room

The biggest thing I understood from this room is that networking isn't just about connecting cables and devices. There are different systems working together to make communication possible.

For example, if a new computer joins a network:

```text
DHCP
 ↓
Gets an IP configuration

ARP
 ↓
Finds the MAC address associated with a local IP

Switch
 ↓
Forwards traffic within the LAN

Router
 ↓
Forwards traffic toward another network
```

Seeing these concepts together made the networking process easier for me to understand.

I also learned that network design matters. A network can be designed for low cost, scalability, reliability, or better segmentation, and different topologies have different trade-offs.

---

# Conclusion

The **Intro to LAN** room took the basic networking concepts from the previous room and went deeper into how local networks are actually organised.

The practical topology exercise helped me see that different network designs have different failure points. I also learned the basics of subnetting and why networks can be divided into smaller sections.

The ARP section helped me understand the relationship between **IP addresses and MAC addresses**, while DHCP showed me how devices can automatically receive network configuration when they join a network.

The main concepts I am taking forward are:

```text
Topology
    ↓
How devices are arranged

Subnetting
    ↓
How networks are divided

ARP
    ↓
IP → MAC mapping

DHCP
    ↓
Automatic IP configuration

Switch
    ↓
Connects devices within a LAN

Router
    ↓
Connects different networks
```

The next room in my learning path is **OSI Model**.