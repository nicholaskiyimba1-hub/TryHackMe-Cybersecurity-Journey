# What Is Networking? Room

## Introduction

This room was my introduction to the basic concepts of **computer networking**.

Before doing this room, I understood networking mainly as devices being connected together, but this room helped me understand what that actually means in computing and how devices identify and communicate with each other.

The main things I learned were:

- What a network is
- What the Internet is
- Private and public networks
- IP addresses
- MAC addresses
- IPv4 and IPv6
- MAC address spoofing
- Ping and ICMP

---

# Task 1: What Is Networking?

A network is basically a group of things that are connected together.

This idea isn't limited to computers. For example, a public transportation system is a network because different parts are connected and work together. The same idea applies to computer networks.

In computing, a network can contain anything from just a few devices to billions of devices.

Examples of network-connected devices include:

- Computers
- Phones
- Security cameras
- Traffic lights
- Servers
- Other network-enabled devices

This is important in cybersecurity because almost everything we interact with digitally depends on some form of networking.

### Key Point

The key term for devices that are connected together is:

**Network**

---

# Task 2: What Is the Internet?

The Internet can be thought of as a **network of networks**.

A small network could consist of computers and other devices connected together privately. Many of these smaller networks can then connect to other networks, eventually forming the much larger public network that we call the Internet.

So I understood the relationship as:

```text
Devices
   ↓
Private Network
   ↓
Other Networks
   ↓
Internet
```

## Public vs Private Networks

The room introduced two basic types of networks:

### Private Network

A private network is a network used by a limited group of devices.

For example, the devices connected to my home router can communicate with each other using their private network addresses.

### Public Network

A public network connects different private networks together. The Internet is the major example.

The important idea I took from this task is that the Internet isn't just one giant physical network. It is made up of many smaller networks that are interconnected.

## World Wide Web

The room also introduced the history of the Internet and the **World Wide Web**.

The World Wide Web was invented by **Tim Berners-Lee**.

One thing I noticed here is that the Internet and the World Wide Web aren't exactly the same thing. The Internet is the underlying global network, while the Web is one of the services that operates over it.

### Answer

**Who invented the World Wide Web?**

**Tim Berners-Lee**

---

# Task 3: Identifying Devices on the Network

For devices to communicate with each other, they need ways to identify one another.

The two main identifiers introduced in this task were:

1. **IP address**
2. **MAC address**

I found the comparison to human identification useful:

```text
Human
├── Name
└── Fingerprint

Network Device
├── IP Address
└── MAC Address
```

The IP address can change, while the MAC address is associated with the device's network interface.

---

## IP Addresses

IP stands for:

**Internet Protocol**

An IP address identifies a device on a network.

An IPv4 address is divided into four sections called **octets**.

For example:

```text
192.168.1.77
```

can be viewed as:

```text
192 . 168 . 1 . 77
 ↑     ↑    ↑    ↑
Octet Octet Octet Octet
```

Therefore, an IPv4 address contains **4 octets**.

---

## Private and Public IP Addresses

I learned that a device can have a private IP address for communication inside its local network and a public IP address for communication across the Internet.

For example:

```text
Device A
Private IP: 192.168.1.77
Public IP: 86.157.52.21

Device B
Private IP: 192.168.1.74
Public IP: 86.157.52.21
```

The two devices can communicate with each other using their private addresses.

When they communicate with the Internet, they can appear to use the same public IP address.

This helped me understand why the IP address I see inside a local network can be different from the public IP address associated with the network.

---

# IPv4

The version of IP addressing that I focused on here was **IPv4**.

IPv4 uses 32 bits, giving a theoretical total of:

```text
2^32 = 4,294,967,296
```

possible addresses.

The problem is that there are far more Internet-connected devices than the available IPv4 address space can comfortably support.

---

# IPv6

IPv6 was introduced to provide a much larger address space.

IPv6 uses **128 bits**, giving:

```text
2^128
```

possible addresses.

The main reason I took away for IPv6 is that it provides a vastly larger address space than IPv4.

---

# MAC Addresses

MAC stands for:

**Media Access Control**

A MAC address is associated with a device's physical network interface.

An example of a MAC address is:

```text
a4:c3:f0:85:ac:2d
```

It is represented using hexadecimal characters and is divided into six groups.

The first part identifies the manufacturer, while the remaining portion identifies the network interface.

---

# MAC Address Spoofing

One of the more interesting parts of this task was **MAC address spoofing**.

MAC spoofing means making a network device appear to have a different MAC address.

The practical lab demonstrated this using a hotel Wi-Fi scenario.

Alice had paid for Wi-Fi, so her traffic was allowed through the network. Bob had not paid, so his packets were blocked.

The idea was to change Bob's MAC address so that it matched Alice's.

After spoofing the MAC address, the network treated Bob's device as if it were Alice's device.

The flag I obtained from the lab was:

```text
THM{YOU_GOT_ON_TRYHACKME}
```

### Why This Matters in Cybersecurity

This showed me why relying only on MAC addresses for authentication or access control can be dangerous.

If a security system assumes that a particular MAC address automatically represents a trusted device, an attacker may be able to impersonate that device by spoofing its MAC address.

---

# Task 4: Ping and ICMP

The next concept I learned was **ping**.

Ping is a basic networking utility used to test whether another device can be reached and to measure the response time.

Ping uses:

**ICMP — Internet Control Message Protocol**

The basic idea is:

```text
My Device
    |
    | ICMP Echo Request
    ↓
Target Device
    |
    | ICMP Echo Reply
    ↓
My Device
```

The time between sending the request and receiving the reply can be used to determine the round-trip time.

---

## Using Ping

The basic syntax is:

```bash
ping <IP address or hostname>
```

For example:

```bash
ping 10.10.10.10
```

I also used the task's target to ping:

```bash
ping 8.8.8.8
```

The room explained that `8.8.8.8` can be used as a reachable Internet address for testing connectivity.

The ping exercise revealed a flag when the correct address was pinged.

---

# Key Things I Learned

This room gave me several networking fundamentals that I will need for the rooms that follow.

| Concept | What I learned |
|---|---|
| Network | Connected devices |
| Internet | A network of networks |
| IP | Internet Protocol |
| IPv4 | Uses four octets |
| Octet | One section of an IPv4 address |
| IPv6 | Uses a much larger address space |
| MAC | Media Access Control |
| MAC address | Identifier associated with a network interface |
| MAC spoofing | Making a device appear to have another MAC address |
| Ping | Tool for testing network connectivity |
| ICMP | Protocol used by ping |

---

# Questions and Answers

### What is the key term for devices that are connected together?

**Network**

### Who invented the World Wide Web?

**Tim Berners-Lee**

### What does IP stand for?

**Internet Protocol**

### What is each section of an IP address called?

**Octet**

### How many sections does an IPv4 address have?

**4**

### What does MAC stand for?

**Media Access Control**

### What protocol does ping use?

**ICMP**

### What is the syntax to ping 10.10.10.10?

```bash
ping 10.10.10.10
```

### What flag was obtained from the MAC spoofing lab?

```text
THM{YOU_GOT_ON_TRYHACKME}
```

---

# Conclusion

This room gave me a much better foundation for understanding networking.

The biggest thing I took from it is that networking is basically about **devices communicating with each other using agreed methods and identifiers**.

I learned that IP addresses help identify devices on networks, while MAC addresses identify network interfaces at a lower level. I also learned the difference between private and public IP addresses and why IPv6 was needed to solve the limitations of IPv4.

The MAC spoofing lab was particularly useful because it showed me that an identifier such as a MAC address should not automatically be treated as proof that a device is trusted.

Finally, learning `ping` and ICMP gave me my first practical networking command for checking connectivity.

The next room I was directed to continue with was **Intro to LAN**.