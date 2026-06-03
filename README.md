# Networking Fundamentals – TryHackMe Write-up

## Overview
This repository documents my hands-on learning experience from the **"What is Networking"** lab on TryHackMe.

The purpose of this project is to build a solid foundation in networking, which is essential for understanding cybersecurity concepts such as system communication, attack surfaces, and network-based threats.

---

## Lab Link
https://tryhackme.com/room/whatisnetworking

---

## Objectives
- Understand what a computer network is  
- Learn how devices communicate over a network  
- Explore key networking concepts used in cybersecurity  

---

## Key Concepts Learned

### 1. What is a Network
A network is a group of interconnected devices that communicate to share data and resources.

![Network Concept](screenshots/screenshot1.png)

---

### 2. IP Addressing
Each device on a network has a unique IP address used for identification and communication.

- Example: 192.168.1.1  
- Enables devices to send and receive data  

![IP Address](screenshots/screenshot2.png)

---

### 3. DNS (Domain Name System)
DNS translates human-readable domain names into IP addresses.

- Example: google.com → IP address  
- Makes it easier for users to access websites  

![DNS](screenshots/screenshot3.png)

---

### 4. Data Transmission
Data is transmitted in packets across networks.

- Source → Router → Destination  
- Packets are reassembled at the destination  

![Data Flow](screenshots/screenshot4.png)

---

## Why Networking Matters in Cybersecurity
Networking is a core part of cybersecurity because:

- Many attacks occur over networks  
- Security professionals monitor network traffic  
- Misconfigured networks can be exploited by attackers  

---

## Skills Gained
- Basic networking knowledge  
- Understanding of IP addressing and DNS  
- Awareness of how data moves across networks  
- Foundation for further cybersecurity learning  

---

## Tools Used
- TryHackMe  
- Linux (basic usage)

---

## Proof of Completion
(Add your completion screenshot below)

![Completion](screenshots/screenshot5.png)

---

## My Reflection
This lab helped me understand how networking forms the foundation of cybersecurity. It also showed me how attackers can take advantage of weak or misconfigured network systems.

---

## Author
Nicholas Kiyimba  
Cybersecurity Student | TryHackMe Learner

INTRODUCTION TO LAN (LOCAL AREA NETWORK)-TryHack Me Writeup

A LAN (Local Area network ) refers to the type of network that is organised a around a small geographical area froexample a school, home a business and among others.

A Network Topology;

A network topology refers to the physical arrangement of computers on a network.

There are many diferent network toplogies used in various organisations.these include;

Ring topology

Bus topology

Star topology

Mesh topology 

Ring topology;

computers or the nodes are arranged in a form of a ring and  if one the physical connector or one computer breaksdown,the whole network is down.

Bus topology

Withisone, the nodes are arranged and connected arround one long physiacal cablle line.
This kind of topology is way cheap and easy to install and relatively cheap.
But the big problem with it is that i cant mange to handle large amounts of data

Star topology

This topology involves nodes being conected to one central networking device like a switch or hub in form of a star.
The advatage they have is that if one single node gets a problem or breaks down, the rest of the nodes stay up and running smothly but if the central networking device to which they are connected forexample a switch breaksdown,the whole network bresks down.

Mesh topology

This refers to the tpye of network topology where where nodes or he computers a arranged in form of a mesh.
With topology,every node interconnected to another node meanig each node has the ability to send and recieve data to each and every node on the network.
this kind of topoogy cant easily breakdown simply because one brokeen node can't affect the other nodes on the network.

SWITCH

This refers to a device that conneccts other network capable devices within a network using an ehterne cable.

ROUTER

A ruoter refers to a networking device that connects networks together and pass or route data between them.

SUBNETTING 

This refers to the splittingup of a network into smaller networks within itself.

network administrators use subneting to categorise and assign specific parts of a network and this is achieved by splitting up the number of hosts that can fit within the network represented by a number called a subnet mask.

PARTS OF AN IP ADDRESS WITH REFERENCE FROM GPT

# IP Address Basics

## What is an IP Address?

An IP (Internet Protocol) address is a unique identifier assigned to a device on a network. It allows devices to communicate with each other.

Example IPv4 Address:

192.168.1.10

---

## Parts of an IPv4 Address

An IPv4 address consists of four parts called **octets** separated by dots.

Example:

192.168.1.10

| Octet | Value |
|--------|--------|
| 1st Octet | 192 |
| 2nd Octet | 168 |
| 3rd Octet | 1 |
| 4th Octet | 10 |

Each octet can have a value from 0 to 255.

---

## Network Portion and Host Portion

An IP address is divided into:

1. Network Portion
2. Host Portion

Example:

IP Address: 192.168.1.10

Subnet Mask: 255.255.255.0

Network Portion: 192.168.1

Host Portion: 10

---

## Real-Life Analogy

Think of a hostel:

- Hostel Block = Network Portion
- Room Number = Host Portion

Example:

Hostel Block A = 192.168.1

Room 10 = 10

Therefore:

192.168.1.10

means Room 10 in Hostel Block A.

---

## IP Address Classes

| Class | First Octet Range | Default Subnet Mask |
|---------|---------|---------|
| A | 1 - 126 | 255.0.0.0 |
| B | 128 - 191 | 255.255.0.0 |
| C | 192 - 223 | 255.255.255.0 |
| D | 224 - 239 | Multicast |
| E | 240 - 255 | Experimental |

Examples:

- Class A: 10.0.0.1
- Class B: 172.16.0.1
- Class C: 192.168.1.1

---

## Special IP Addresses

### Loopback Address

127.0.0.1

Also called localhost.

Used by a computer to communicate with itself.

### Private IP Addresses

Private IP ranges:

- 10.0.0.0 – 10.255.255.255
- 172.16.0.0 – 172.31.255.255
- 192.168.0.0 – 192.168.255.255

These addresses are used inside private networks.

---

## CIDR Notation

Example:

192.168.1.10/24

The /24 means:

- First 24 bits represent the network.
- Remaining 8 bits represent hosts.

Equivalent subnet mask:

255.255.255.0

---

## Example Analysis

IP Address:

192.168.10.25/24

Analysis:

- 1st Octet = 192
- 2nd Octet = 168
- 3rd Octet = 10
- 4th Octet = 25
- Network Address = 192.168.10.0
- Host ID = 25
- Class C
- Private IP Address

---

## Key Takeaways

- IPv4 addresses contain four octets.
- Each octet ranges from 0 to 255.
- IP addresses contain network and host portions.
- Subnet masks determine the network size.
- CIDR notation simplifies subnet representation.
- Understanding IP addressing is fundamental in networking and cybersecurity.

  Subnet use a device IP addres to identfy the network address, the host address and te default gateway;

  The network address simply identifies the network's existance e.g the device wwith an IP address of 192.168.1.100 will be on the network identified by 192.168.1.0

   The host address identifies the specific device on the subnet represented by a number.e.g device will have a netwok address of 192.168.1.1 with that last one on the IP as the host address. forexample 192.168.1.100

  The default gateway is a special address hat is used  to send information to another network.Any data that needs to  go to anoter device hat is not on the same network i.e 192.168.1.1 will sent to this device by either using the first or last host address in the net work that is eiher 1 or 254. e.g 192.168.1.254

  The broadcast address is that very last number onthe ip address forexample 192.168.1.255, the 255 is the broadcast address and it it is used to send data to all devices on the network at the same time.

  ARP (ADDRESS RESOLUTION PROTOCOL)
  
  This refers to a  protocal that keeps devices speaking the same the same language such they can understand each other.

  itworks thisway,

  it an ARP request and
  An ARP reply

  when the ARP request is addressed tot the network, it asks '' what is the MAC address that owns this IP address'' When other devices recieve hat message, they will only reply only if they they own that IP address and they reply with an ARP reply with its MAC  adddress.
  The requesting device can now emember its mapping ad store it in its ARP cache memory for fututre use.

  DHCP (DYNAMIC HOST CONFIGURATION PROTOCOL)

  I f a device on network does not have an IPAddrss, DHCP server assigns one to it using DHCP

  When a computer connects to a net work, it sends out what we call a DHCP dicover to see if there are nay DHCP servers exiting on the network. If the network has a DHCP server, it replies with a DHDCP offer along with an IP address. When the computeer recieves the DHPCP offer,it replies with a DHCP request to the server.When the request recheaches the server,it sends a DHCP ACK acknowledging the computer to use thw IP it has benn given.


  
  
