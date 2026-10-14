# Router Configuration Library

This page is the central entry point for router configuration work in the repository. Each project keeps its authoritative configuration or guide with its own topology and supporting files, so a command is not duplicated in multiple places and allowed to drift.

## Project Configurations

| Project | Router configuration material |
|---|---|
| Static NAT and OSPF | [Combined lab guide and command templates](Routing-Protocols/NAT-OSPF-CONFIGURATION/README.md) |
| Hotel Management Network | [R1](lab-04-Hotel-management_network-project/configurations/R1.txt), [R2](lab-04-Hotel-management_network-project/configurations/R2.txt), and [R3](lab-04-Hotel-management_network-project/configurations/R3.txt) exported configurations. |
| Secure Company Network | [IOS OSPF router template](lab-05-Secure-company-network/NOTEPAD/ospf-router-template.md) and [OSPF neighbor verification](lab-05-Secure-company-network/NOTEPAD/ospf-neighbor-verification.md). |

## Before Applying a Configuration

1. Open the project's `.pkt` file and verify the device model, interface names, and addressing plan.
2. Replace template values and placeholders with values confirmed for that topology.
3. Check that credentials and other secrets are removed before sharing exported configurations.
4. Verify the configuration with the project's documented show commands and connectivity tests.

The hotel files are exported configurations. The NAT/OSPF and Lab 5 documents contain project-specific guides or reusable templates; they are not complete device exports unless explicitly stated.