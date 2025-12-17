

# Static Routing Implementation using EVE-NG
---

 ![3D](/Images/Static.png) 

 ---
 
## 📌 Overview
This repository contains an **EVE-NG lab implementation of Static Routing** using Cisco routers.  
The lab demonstrates how static routes are manually configured to enable communication between multiple networks without using dynamic routing protocols.

This project is designed for **CCNA/CCNP learners**, networking students, and beginners who want hands-on practice with routing concepts.

---

## 🧠 Objectives
- Understand the concept of **Static Routing**
- Configure **IP addressing** on router interfaces
- Implement **static routes** between different networks
- Verify connectivity using **ping** and **traceroute**
- Analyze packet flow across the topology

---

## 🛠 Tools & Technologies
- **EVE-NG Community Edition**
- **Cisco IOS Routers**
- **VPCS (Virtual PC Simulator)**
- Networking protocols: **IP, ICMP**

---

## 🗺 Network Topology
The lab consists of multiple routers connected in series, with each router serving a different network segment.

## 🗺  Static Route Configured R1 --> R3 --> R5 --> R6

## Configurations on Nodes

## R1

hostname R1

version 15.2

!
! Interface Configuration
!

interface FastEthernet0/0
 no ip address
 shutdown
 duplex full

interface Ethernet1/0
 ip address 192.168.13.1 255.255.255.0
 duplex full

interface Ethernet1/1
 ip address 192.168.12.1 255.255.255.0
 duplex full

interface Ethernet1/2
 ip address 192.168.1.254 255.255.255.0
 duplex full



!
! Static Routing
!

ip route 192.168.6.0 255.255.255.0 192.168.13.3

## R3

hostname R3

version 15.2
!
! Interface Configuration
!
interface Ethernet1/0
 ip address 192.168.13.3 255.255.255.0
 duplex full

interface Ethernet1/1
 ip address 192.168.35.3 255.255.255.0
 duplex full

interface Ethernet1/2
 ip address 192.168.34.3 255.255.255.0
 duplex full

interface Ethernet1/3
 ip address 192.168.60.3 255.255.255.0
 duplex full


!
! Static Routing Configuration
!

ip route 0.0.0.0 0.0.0.0 192.168.60.1

ip route 192.168.1.0 255.255.255.0 192.168.13.1

ip route 192.168.6.0 255.255.255.0 192.168.35.5

ip route 192.168.60.0 255.255.255.0 192.168.13.1


## R5

hostname R5

version 15.2

interface Ethernet1/0
 ip address 192.168.35.5 255.255.255.0
 duplex full

interface Ethernet1/1
 ip address 192.168.56.5 255.255.255.0
 duplex full

interface Ethernet1/2
 ip address 192.168.5.254 255.255.255.0
 duplex full

!
! Static Routing Configuration
!

ip route 192.168.1.0 255.255.255.0 192.168.35.3

ip route 192.168.6.0 255.255.255.0 192.168.56.6


## R6

hostname R6

version 15.2
!
! Loopback Interface
!

interface Loopback0
 ip address 10.0.0.1 255.255.255.0

!
! Physical Interface Configuration
!

interface Ethernet1/0
 ip address 192.168.46.6 255.255.255.0
 duplex full

interface Ethernet1/1
 ip address 192.168.56.6 255.255.255.0
 duplex full

interface Ethernet1/2
 ip address 192.168.6.254 255.255.255.0
 duplex full

!
! Static Routing Configuration
!

ip route 192.168.1.0 255.255.255.0 192.168.56.5

## PC12
Device Name : VPCS[1]

IP Address  : 192.168.1.2
Subnet Mask : 255.255.255.0
Default GW  : 192.168.1.254

DNS Server  : Not configured
MAC Address : 00:50:79:66:68:0b
MTU         : 1500


## PC 15

Device Name   : VPCS[1]

IP Address    : 192.168.6.1
Subnet Mask   : 255.255.255.0
Default GW    : 192.168.6.254

DNS Server    : Not configured
MAC Address   : 00:50:79:66:68:0f
MTU           : 1500



---

