# Core Switch VLANs and Trunks

VLANs separate Layer 2 broadcast domains. Trunks carry multiple VLANs between network devices; only configure a trunk on links that are intended to carry those VLANs.

The Lab 5 notes and requirements identify VLANs 10, 20, 50, 70, and 199. VLAN 90 for inside servers also appears in the saved switch configuration and HSRP capture.

```text
configure terminal
vlan 10
 name MGT
vlan 20
 name LAN
vlan 50
 name WLAN
vlan 70
 name VOIP
vlan 90
 name INSIDE-SERVERS
vlan 199
 name BLACKHOLE
```

Example trunk range from the original note; confirm the exact port roles first:

```text
interface range GigabitEthernet1/0/3 - 8
 switchport mode trunk
```

On platforms with fixed 802.1Q trunking, `switchport trunk encapsulation dot1q` is unavailable and unnecessary. Verify trunks and VLANs with `show interfaces trunk` and `show vlan brief`.
