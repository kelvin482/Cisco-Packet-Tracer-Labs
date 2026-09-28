# Lab 5 Command Notes

These notes document the Secure Company Network Packet Tracer project. They explain each feature, show cleaned command examples, and call out settings that still need confirmation in the `.pkt` file.

## Addressing and VLANs

| Segment | VLAN | Network | Notes |
|---|---:|---|---|
| Management | 10 | `192.168.10.0/24` | Confirmed by the project addressing supplied for this lab and the HSRP capture. |
| LAN | 20 | `172.16.0.0/16` | User supplied. |
| WLAN | 50 | `10.20.0.0/16` | User supplied. |
| Voice | 70 | `172.30.0.0/16` | User supplied. |
| DMZ | Not specified | `10.11.11.0/27` | The DMZ interface/subnet is documented; its VLAN ID is not established here. |
| Inside servers | 90 in captured configs | `10.11.11.32/27` | VLAN 90 appears in the switch notes and HSRP capture. |
| Unused access ports | 199 | Not applicable | Blackhole VLAN from the project requirements. |

## Notes

| Topic | File |
|---|---|
| Access and voice VLANs | [voice-vlan-access-port.md](voice-vlan-access-port.md) |
| Switch VLANs and trunks | [access-switch-vlans.md](access-switch-vlans.md), [core-switch-vlan-and-trunk.md](core-switch-vlan-and-trunk.md), [server-switch-vlans.md](server-switch-vlans.md) |
| OSPF | [ios-ospf-core-switch.md](ios-ospf-core-switch.md), [ospf-router-template.md](ospf-router-template.md), [ospf-neighbor-verification.md](ospf-neighbor-verification.md) |
| HSRP | [hsrp-core-gateways.md](hsrp-core-gateways.md) |
| EtherChannel and STP | [etherchannel-lacp.md](etherchannel-lacp.md), [stp-edge-port-protection.md](stp-edge-port-protection.md) |
| ASA firewall | [asa-outside-interface.md](asa-outside-interface.md), [asa-static-routes-and-ospf.md](asa-static-routes-and-ospf.md), [asa-nat-reference.md](asa-nat-reference.md), [asa-nat-lab-mappings.md](asa-nat-lab-mappings.md), [asa-acl-policy.md](asa-acl-policy.md), [asa-acl-examples.md](asa-acl-examples.md) |
| Device administration | [switch-ssh-management.md](switch-ssh-management.md) |
| General examples from the original notebook | [general-ios-command-notebook.md](general-ios-command-notebook.md) |

## Validation status

The subnet values above are the lab owner's confirmed addressing. CLI examples are syntax-cleaned from the notes and captured evidence, but should still be checked against the device model and current running configuration in Packet Tracer before pasting them into a device. The ISP2 next-hop address and the intended firewall ACL policy remain unconfirmed; the related notes use placeholders or identify the policy question instead of choosing values.

The original scratch copies at the repository root were not changed.
