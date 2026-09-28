# Configure an Access Port for a PC and IP Phone

An access port can carry a PC's data traffic in one access VLAN and a phone's tagged voice traffic in a separate voice VLAN. This keeps voice and user data logically separated while both devices share a switch port.

For Lab 5, the documented data VLAN is 20 and the voice VLAN is 70. Apply this only to ports that actually connect to an IP phone and a PC.

```text
configure terminal
interface range FastEthernet0/5 - 6
 switchport mode access
 switchport access vlan 20
 switchport voice vlan 70
end
copy running-config startup-config
```

The old note used `no switchport access vlan 70`, which removes VLAN 70 as the data access VLAN; it does not assign the intended data VLAN. Use the explicit access and voice VLAN commands above.

Check the result with `show interfaces switchport` and `show vlan brief`. Confirm the selected interfaces and VLAN database before applying the range.

Reference: [Cisco Catalyst Voice VLAN Configuration](https://www.cisco.com/c/en/us/support/docs/switches/catalyst-2950-series-switches/113260-voice-vlan-00.pdf).
