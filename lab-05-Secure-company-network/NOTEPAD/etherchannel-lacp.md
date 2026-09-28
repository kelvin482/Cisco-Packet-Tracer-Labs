# Build a Trunk EtherChannel with LACP

LACP negotiates an EtherChannel from compatible physical links. The bundle provides more aggregate bandwidth and link resilience; it does not make a single flow exceed one member link's capacity.

Configure matching member interfaces at both ends. The following ports and channel number come from the original note; verify that these are the intended links:

```text
configure terminal
interface range GigabitEthernet1/0/9 - 11
 channel-group 1 mode active
exit
interface Port-channel1
 switchport mode trunk
end
copy running-config startup-config
```

`switchport mode trunk` corrects the original typo `switchort`. Ensure both ends use compatible speed, duplex, trunk settings, and allowed VLANs. Configure a port-channel only if the switch model and Packet Tracer device support the selected interfaces.

Verify with `show etherchannel summary` and `show interfaces trunk`.
