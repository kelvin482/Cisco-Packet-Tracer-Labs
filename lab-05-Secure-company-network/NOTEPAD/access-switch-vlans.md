# Access Switch VLANs and Unused Ports

Access VLANs place endpoint ports in the correct broadcast domain. Trunk links carry multiple VLANs toward another switch or network device. Unused ports can be placed in a dedicated blackhole VLAN and administratively shut down.

This example follows the original port map. Confirm each port's role before applying it:

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
vlan 199
 name BLACKHOLE
!
interface range FastEthernet0/1 - 2
 switchport mode trunk
!
interface range FastEthernet0/3 - 4
 switchport mode access
 switchport access vlan 20
!
interface range FastEthernet0/5 - 6
 switchport mode access
 switchport access vlan 20
 switchport voice vlan 70
!
interface FastEthernet0/7
 switchport mode access
 switchport access vlan 50
!
interface range FastEthernet0/8 - 24, GigabitEthernet0/1 - 2
 switchport mode access
 switchport access vlan 199
 shutdown
end
copy running-config startup-config
```

The original note assigned ports 5-6 to VLAN 70 as the data VLAN. The lab requirement identifies VLAN 70 as voice, so this cleaned version keeps data on VLAN 20 and uses `switchport voice vlan 70`. Confirm whether those ports connect to phones and PCs. The DMZ and server VLAN assignments are not inferred here.

Verify with `show vlan brief`, `show interfaces trunk`, and `show interfaces status`.
