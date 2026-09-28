# Lab 5 NAT Mapping Inventory

The original NAT notes record PAT for the LAN, WLAN, and DMZ networks through two inside and two outside ASA interfaces. The network objects below use the confirmed Lab 5 subnets. The interface combinations are preserved from the notes and must be checked against the active ASA topology before use.

| Object suffix | Source subnet | Interface pair in scratch notes |
|---|---|---|
| `LAN-OUTSIDE1` | `172.16.0.0/16` | `(INSIDE1,OUTSIDE1)` |
| `LAN-OUTSIDE2` | `172.16.0.0/16` | `(INSIDE1,OUTSIDE2)` |
| `LAN-INSIDE2-OUTSIDE1` | `172.16.0.0/16` | `(INSIDE2,OUTSIDE1)` |
| `LAN-INSIDE2-OUTSIDE2` | `172.16.0.0/16` | `(INSIDE2,OUTSIDE2)` |
| `WLAN-OUTSIDE1` | `10.20.0.0/16` | `(INSIDE1,OUTSIDE1)` |
| `WLAN-OUTSIDE2` | `10.20.0.0/16` | `(INSIDE1,OUTSIDE2)` |
| `WLAN-INSIDE2-OUTSIDE1` | `10.20.0.0/16` | `(INSIDE2,OUTSIDE1)` |
| `WLAN-INSIDE2-OUTSIDE2` | `10.20.0.0/16` | `(INSIDE2,OUTSIDE2)` |
| `DMZ-OUTSIDE1` | `10.11.11.0/27` | `(DMZ,OUTSIDE1)` |
| `DMZ-OUTSIDE2` | `10.11.11.0/27` | `(DMZ,OUTSIDE2)` |

Example for one mapping:

```text
object network LAN-OUTSIDE1
 subnet 172.16.0.0 255.255.0.0
 nat (INSIDE1,OUTSIDE1) dynamic interface
```

The original ISP2 address/next-hop records conflict with the addressing-plan image. This mapping list does not resolve that issue; verify ISP2 interface addressing and routing in the `.pkt` file. Also confirm that the ASA version accepts the intended set of overlapping source-network objects and that routing selects the same egress interface as the NAT rule.
