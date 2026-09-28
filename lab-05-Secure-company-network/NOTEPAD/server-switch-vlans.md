# Server Access Switch VLANs

This configuration records the port roles in the original server-switch note. It assigns server-facing access ports to VLAN 90 and one access port to WLAN VLAN 50; confirm the physical devices connected to each port before applying.

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
!
interface range FastEthernet0/1 - 2, FastEthernet0/7
 switchport mode trunk
!
interface range FastEthernet0/3 - 5
 switchport mode access
 switchport access vlan 90
!
interface FastEthernet0/6
 switchport mode access
 switchport access vlan 50
end
copy running-config startup-config
```

Trunk and access assignments are kept from the source note. Verify actual uplink and endpoint ports with the topology and `show interfaces trunk` / `show vlan brief` before pasting.
