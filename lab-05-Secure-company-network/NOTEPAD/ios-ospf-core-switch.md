# OSPF on the Core Layer 3 Switch

OSPF advertises connected networks and learns routes from other OSPF routers. It helps the redundant core and firewall exchange routes without maintaining a separate static route for every internal subnet.

The original note identifies OSPF process 35 and router ID `1.1.2.2`. IOS uses wildcard masks in `network` statements. The supplied Lab 5 networks translate to these statements:

```text
router ospf 35
 router-id 1.1.2.2
 network 10.2.2.8 0.0.0.3 area 0
 network 10.2.2.12 0.0.0.3 area 0
 network 192.168.10.0 0.0.0.255 area 0
 network 172.16.0.0 0.0.255.255 area 0
 network 10.20.0.0 0.0.255.255 area 0
 network 172.30.0.0 0.0.255.255 area 0
 network 10.11.11.32 0.0.0.31 area 0
```

The management, LAN, WLAN, and voice networks above use the subnets supplied by the lab owner. The inside-server subnet is from the saved VLAN 90 configuration. The voice statement is included to advertise the supplied voice subnet if VLAN 70 is routed by this switch and OSPF is intended on that SVI; confirm that condition in the project before applying it.

The original note omitted voice and used the old management subnet. The DMZ subnet is not added here because the notes show it on the ASA, not as a core SVI. Verify every statement against `show ip interface brief` and `show ip ospf interface brief`.
