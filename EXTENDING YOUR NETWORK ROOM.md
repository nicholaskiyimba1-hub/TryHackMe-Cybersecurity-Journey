# EXTENDING YOUR NETWORK

## Port forwarding 

Port forwarding refers to the processing of forwarding a port out of the network for a specific purpose.E.g. Say a webserver is hosting a website on port 80 and they want the website to be viewed by other popople on  other networks,they will forward port 80 out of their network

## FIREWALL

This refers to a device within a network that determines what traffic is allowed in or out of the network.

## CATEGORIES OF FIREWALLS

**Statefull firewall**

This firewall uses the entire connection of a device to to dtermine its behaviuor

**Stateless firewalls**

This firewall uses a static set of rules to determine whether individual packets are acceptable or not.

## VPNs (Virtual Private Networks)

This refers to a tchnology that allows 2 devices on seperate networks to communicate securely by creating a dedicated path between each other over the internet knownas a "Tunnel"

## The following are some of the existing VPN technologies.

**PPP(Point-to-Point Protocol)**

PPP (Point-to-Point Protocol) is a data link layer (Layer 2) communication protocol used to establish a direct connection between two nodes over a serial link. It is foundational to many VPN technologies.

Therefore this technology is used by **PPTP** to allow for authentication and  provide encryption of data

**NOTE** that the PPP itself is not a VPN protocol, but it is the underlying transport for several VPN technologies therefore its non-routable or is not cpable of leaving the network by itself.

**PPTP( Point To Point Tunnelling Protocol )**

This is the protocol that allows the data from PPP to travel and leave the network.

**IPSec (Internet Protocol Security)**

This one is responsible for encrypting data using the existing  Internet Protocol Framework.
It is is diffivult to setup in cmparison with the other alternatatives. However, if successfull, it boosts a strong encryption and is copatible with many devices.

**VLAN (Virtual Local Area Networks)**

This a technologhy that allows specific devices within a network to be **virtually split up**. This improves the security of the network by determining which devices communincate to each other on the network.
