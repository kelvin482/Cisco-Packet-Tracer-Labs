# Static NAT Configuration

A Cisco Packet Tracer lab demonstrating a small internal LAN connected through a NAT router to an ISP and an external test server.

## Topology

The supplied diagram labels these network segments:

| Segment | Network shown |
|---|---|
| Internal LAN | `192.168.20.0/24` |
| NAT router to ISP | `200.100.50.0/30` |
| External test-server network | `8.8.8.0/24` |

The diagram is a visual reference; inspect the Packet Tracer file for the actual interface addressing and device configuration.

![Static NAT lab topology](topology.png)

## Project Files

| File | Description |
|---|---|
| [Static NAT Packet Tracer lab](Static-NAT-configuration.pkt) | Editable network simulation. |
| [Topology diagram](topology.png) | Screenshot of the logical topology. |
| [Configuration and testing](configuration-and-testing.md) | OSPF and Static NAT examples, verification commands, and a before/after test checklist. |
| [Topology and design notes](topology-and-design.md) | Device roles, routing and NAT concepts, and a testing walkthrough. |

## Suggested Workflow

1. Open the `.pkt` file in Cisco Packet Tracer and review the topology and device configurations.
2. Treat the commands in the notes as examples; substitute the addresses and interfaces used by the simulation.
3. Record baseline connectivity and routing before changing the NAT configuration.
4. Verify interface status, routes, and the Static NAT mapping, then generate test traffic and compare the results.

Useful Cisco IOS checks include `show ip interface brief`, `show ip route`, `show ip nat translations`, and `show ip nat statistics`. A configured static mapping can appear before traffic is generated, so check both the mapping and observed connectivity.