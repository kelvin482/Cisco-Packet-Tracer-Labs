# HSRP Virtual Gateways on the Core Switches

HSRP gives clients a virtual default-gateway address shared by two Layer 3 switches. One switch forwards traffic as active; the standby switch can take over if the active switch becomes unavailable.

The captured CORE-SW1 configuration uses these interface addresses and virtual gateways:

| SVI | CORE-SW1 address | HSRP group | Virtual gateway |
|---|---|---:|---|
| VLAN 10 | `192.168.10.2/24` | 10 | `192.168.10.1` |
| VLAN 20 | `172.16.0.2/16` | 20 | `172.16.0.1` |
| VLAN 50 | `10.20.0.3/16` | 50 | `10.20.0.1` |
| VLAN 90 | `10.11.11.35/27` | 90 | `10.11.11.33` |

Example from the saved CORE-SW1 note:

```text
interface Vlan10
 ip address 192.168.10.2 255.255.255.0
 ip helper-address 10.11.11.38
 standby 10 ip 192.168.10.1
```

Use the corresponding interface addresses and HSRP group on CORE-SW2; its addresses in the capture end in `.3` for VLANs 10 and 20, `.2` for VLAN 50, and `.34` for VLAN 90. The virtual IP remains the same on both switches. The capture shows CORE-SW1 active and CORE-SW2 standby.

The saved HSRP configuration does not show VLAN 70. Do not infer a voice SVI or HSRP group from the subnet alone. Confirm voice gateway configuration in the project before adding it.

Verify with `show standby brief` from privileged EXEC mode. The DHCP relay address `10.11.11.38` is present in the saved config for client VLANs; confirm the DHCP server address in the current project.

Reference: [Cisco IOS XE HSRP Configuration Guide](https://www.cisco.com/c/en/us/td/docs/routers/ios-xe/network-services/network-services/m_fhp-hsrp-0.html).
