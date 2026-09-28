# Verify OSPF Neighbors

OSPF neighbors show whether routers or Layer 3 switches have formed an adjacency and can exchange route information. A `FULL` state is the expected fully adjacent state for the neighbors shown in this lab capture.

Run these commands from privileged EXEC mode (`#`), not global configuration mode (`(config)#`):

```text
show ip ospf neighbor
show ip ospf interface brief
show ip route ospf
```

The saved capture shows neighbor ID `1.1.2.2` in `FULL/DR` state on VLAN interfaces 10, 20, 50, and 90. Treat this as a snapshot, not a guarantee that the current project still has the same state.

If a neighbor is absent or not `FULL`, check interface state and addressing, matching OSPF area settings, OSPF network statements, and whether OSPF is enabled on the connecting interfaces. Useful checks include `show ip interface brief`, `show ip ospf interface`, and `show ip route`.
