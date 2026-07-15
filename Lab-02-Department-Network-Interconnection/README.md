# Lab 02 - Department Network Interconnection

## Overview

This lab demonstrates how to interconnect two departmental Local Area Networks (LANs) using a Cisco 2901 Router and Cisco 2960 switches. The objective is to enable communication between devices located in different IP subnets through proper router configuration.

---

## Objectives

- Design a small enterprise network
- Configure IPv4 addressing
- Subnet a /24 network into two /25 networks
- Configure router interfaces
- Configure default gateways
- Verify end-to-end connectivity
- Test communication using ICMP (Ping)

---

## Network Topology

Departments:

- Accounts
- Transport

Devices:

- Cisco 2901 Router
- Two Cisco 2960 Switches
- Four PCs
- Two Network Printers

---

## IP Addressing

| Department | Network | Subnet Mask | Default Gateway |
|------------|---------|-------------|-----------------|
| Accounts | 192.168.40.0/25 | 255.255.255.128 | 192.168.40.1 |
| Transport | 192.168.40.128/25 | 255.255.255.128 | 192.168.40.129 |

---

## Skills Learned

- IPv4 Addressing
- Subnetting
- Cisco IOS Configuration
- Router Configuration
- Switch Configuration
- Default Gateway Configuration
- Network Verification
- ICMP Testing
- Basic Troubleshooting

---

## Verification

Successful tests include:

- PC to PC communication
- PC to Printer communication
- Inter-department communication
- Successful ICMP Echo Replies

---

## Troubleshooting

Commands used:

```bash
show ip interface brief
show ip route
ping
ipconfig
```

---

## Lessons Learned

- Routers connect different networks.
- Switches connect devices within the same network.
- Correct IP addressing and default gateways are essential for successful communication.
- Simulation Mode in Packet Tracer is valuable for observing packet flow.

---


Cisco Packet Tracer Labs Repository
