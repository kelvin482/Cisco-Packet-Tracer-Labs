# University Network - Cisco Packet Tracer

## Overview

This project is a prototype of a multi-campus university network designed and implemented in Cisco Packet Tracer.

The network connects the main campus, a smaller branch campus, internal servers, and an externally hosted email server. The design uses VLANs, Layer 3 switching, routing protocols, DHCP, and static routing to provide communication between different departments and network segments.

## Network Structure

The network consists of:

- Main Campus
	- Building A - Administration, HR, Finance, and Business
	- Building B - EAC and A/D departments
	- Building C - Student Labs and IT Department
- Branch Campus
	- Staff network
	- Student Lab
- Internal university servers
	- Web server
	- FTP server
- External cloud network
	- Email server
- Main campus router
- Branch router
- Layer 3 switches
- Access switches
- PCs and printers

## VLAN Segmentation

Separate VLANs were created to logically isolate the different departments and user groups.

| VLAN | Network | Purpose |
|------|---------|---------|
| VLAN 10 | 192.168.1.0/24 | Administration |
| VLAN 20 | 192.168.2.0/24 | HR |
| VLAN 30 | 192.168.3.0/24 | Finance |
| VLAN 40 | 192.168.4.0/24 | Business |
| VLAN 50 | 192.168.5.0/24 | EAC |
| VLAN 60 | 192.168.6.0/24 | A/D |
| VLAN 70 | 192.168.7.0/24 | Student Lab |
| VLAN 80 | 192.168.8.0/24 | IT Department |
| VLAN 90 | 192.168.9.0/24 | Branch Staff |
| VLAN 100 | 192.168.10.0/24 | Branch Student Lab |

VLANs provide network segmentation and help reduce unnecessary broadcast traffic between departments.

## Routing

### Inter-VLAN Routing

Layer 3 switches are used to provide communication between the VLANs.

Each VLAN has its own IP network and default gateway, allowing devices in different departments to communicate where permitted.

### RIPv2

RIPv2 is configured between the internal routers to exchange routes between the main campus and branch network.

This allows the routers to dynamically learn the networks available through the other router.

### Static Routing

Static routing is used for connectivity toward the external cloud network where the university email server is hosted.

The cloud network uses `20.0.0.0/30`.

## DHCP

A router-based DHCP service was configured for the Administration/Building A network.

This allows client devices to automatically obtain:

- IP address
- Subnet mask
- Default gateway
- Other required network information

This reduces the need to manually configure IP addresses on individual client devices.

## Switching

The access switches are configured with VLANs and connected to the Layer 3 switches.

Trunk links are used where multiple VLANs need to travel across a single physical connection between switches and the Layer 3 switching infrastructure.

Access ports are assigned to the appropriate VLAN for end devices such as PCs and printers.

## WAN / Router Connections

Point-to-point router links use `/30` networks to provide efficient addressing for router-to-router communication.

Examples used in the topology include:

- `10.10.10.0/30` - main router to branch router
- `10.10.10.4/30` - cloud/main campus connection

The `/30` networks provide two usable IP addresses, which is suitable for point-to-point links.

## Servers

The network includes internal university servers for services such as:

- Web hosting
- FTP

An external email server is represented in the cloud network.

## Connectivity Testing

Connectivity was tested between different parts of the network using tools and commands such as:

- `ping`
- `ipconfig`
- `show ip route`
- `show vlan brief`
- `show interfaces trunk`
- `show ip interface brief`

These tests were used to verify addressing, VLAN configuration, routing, and end-to-end connectivity.

## Key Networking Concepts Implemented

- VLAN segmentation
- 802.1Q trunking
- Access ports
- Layer 3 switching
- Inter-VLAN routing
- RIPv2 dynamic routing
- Static routing
- Router-based DHCP
- IPv4 subnetting
- `/30` point-to-point networks
- Client/server connectivity
- Basic network troubleshooting

## Tools Used

- Cisco Packet Tracer
- Cisco IOS CLI

## Project Status

The topology has been designed and configured as a working Cisco Packet Tracer prototype, with routing, VLAN segmentation, DHCP, server connectivity, and inter-campus communication implemented and tested.
