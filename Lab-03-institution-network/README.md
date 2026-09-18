# Lab 03 - Institution Network

## Overview

This project models a complete institution network in Cisco Packet Tracer. It connects multiple buildings and departments at a main campus, links the campus to a remote branch, and provides shared network services through an external cloud segment.

The design focuses on VLAN segmentation, inter-VLAN routing, routed campus-to-branch connectivity, and the use of centralized network services.

## Network Topology

The institution is divided into three main campus buildings and one branch location:

- **Building A:** Administration, HR, Finance, and Business
- **Building B:** EAC and A/D departments
- **Building C:** Student Lab, IT Department, and a second student lab
- **Branch:** Staff and student lab networks
- **Cloud services:** Email server connected through a cloud router

Network devices include:

- Main campus Cisco 2911 router
- Branch Cisco 2911 router
- Main campus multilayer switch
- Branch multilayer switch
- Cisco 2960 access switches
- PCs, printers, and application servers

## VLAN and IP Addressing Plan

Each department is placed in its own VLAN and IPv4 subnet:

| VLAN | Department or Network | Subnet |
|------|------------------------|--------|
| 10 | Administration | 192.168.1.0/24 |
| 20 | HR | 192.168.2.0/24 |
| 30 | Finance | 192.168.3.0/24 |
| 40 | Business | 192.168.4.0/24 |
| 50 | EAC | 192.168.5.0/24 |
| 60 | A/D | 192.168.6.0/24 |
| 70 | Student Lab | 192.168.7.0/24 |
| 80 | IT Department | 192.168.8.0/24 |
| 90 | Branch Staff | 192.168.9.0/24 |
| 100 | Branch Student Lab | 192.168.10.0/24 |

The router-to-router links use the `10.10.10.0/30` and `10.10.10.4/30` networks. The cloud segment uses the `20.0.0.0/30` network.

## Services

The topology includes servers for common institution services:

- Email server in the cloud segment
- FTP server in the IT department
- Web server in the IT department

Printers are also placed in several departmental VLANs to represent shared office resources.

## Objectives

- Design a multi-building institution network
- Segment departments with VLANs
- Configure access and multilayer switching
- Enable communication between VLANs
- Connect a main campus to a branch network
- Provide access to centralized network services
- Apply IPv4 addressing and subnetting
- Verify connectivity across local and remote networks

## Skills Demonstrated

- VLAN design and segmentation
- Inter-VLAN routing
- Layer 3 switch configuration
- Router-to-router connectivity
- Access switch configuration
- IPv4 addressing
- Network services integration
- Packet Tracer topology design and troubleshooting

## Verification

The completed Packet Tracer file can be used to test:

- Communication between devices in the same VLAN
- Communication between different departmental VLANs
- Main campus to branch connectivity
- Access to the FTP and web servers
- Email server connectivity through the cloud segment
- Printer reachability from the appropriate departments

Useful verification commands include:

```text
show vlan brief
show interfaces trunk
show ip interface brief
show ip route
ping
traceroute
```

## Project Files

- `INSTITUTION PROJECT.pkt2.pkt` - Cisco Packet Tracer network project
- `Screenshot 2026-09-18 181207.png` - Network topology overview
