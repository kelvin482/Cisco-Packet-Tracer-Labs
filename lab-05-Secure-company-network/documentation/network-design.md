# Network Design

## Requirements

The project requirements are captured in [technical-requirements.png](../screenshots/technical-requirements.png). Add a concise summary here, including any requirements that changed during implementation.

## Architecture

The current project scope includes two ISP connections, a Cisco ASA firewall, multilayer core switches, access switches, wireless LAN controllers, access points, and a server farm.

Add the device roles, department layout, and important physical or logical connections here.

## Segmentation and Addressing

The documented VLANs are management (10), user LAN (20), WLAN (50), VoIP (70), and unused-port blackhole (199). See the [addressing plan](addressing-table.md) for subnet, gateway, and address allocation details.

## Routing and Availability

The documented design uses inter-VLAN routing on multilayer switches, OSPF route exchange, HSRP virtual gateways, DHCP relay on client VLANs, and LACP EtherChannel.

Add the OSPF process and neighbor relationships, HSRP roles and priorities, EtherChannel endpoints, and failover behavior here.

## Security and Services

The documented scope includes SSH-only remote administration with an access control list, firewall policies, spanning-tree protections (PortFast and BPDU Guard), and voice gateway configuration.

Add firewall interface zones and policies, management access rules, wireless security, DHCP scope details, and voice services here.

## Validation Results

Add test steps and observed results for inter-VLAN connectivity, routing, DHCP, wireless access, firewall policy, and redundancy failover.

The current [HSRP verification capture](../screenshots/hsrp-status.png) shows CORE-SW1 active and CORE-SW2 standby for the displayed VLAN interfaces.