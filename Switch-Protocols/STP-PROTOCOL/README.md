# Spanning Tree Protocol Lab

Open `STP-LAB1.pkt` in Cisco Packet Tracer to explore how Spanning Tree Protocol prevents Layer 2 loops when switches have redundant paths.

Inspect the root bridge and the role and state of each switch port. A redundant path may be placed in a non-forwarding state so it remains available if the active path changes.

Use these commands on a switch to verify the topology:

```text
show spanning-tree
show spanning-tree vlan 1
```