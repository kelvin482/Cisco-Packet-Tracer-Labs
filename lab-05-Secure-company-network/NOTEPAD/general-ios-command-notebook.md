# General IOS Command Notebook

This file preserves useful examples from the original mixed-lab notebook. The examples are not all part of Lab 5. Replace sample interfaces, VLANs, addresses, and pool names with values from the target project.

## Access VLAN and trunk examples

```text
configure terminal
interface range FastEthernet0/1 - 24
 switchport mode access
 switchport access vlan 100
exit
```

Use a trunk only on links that must carry multiple VLANs:

```text
interface GigabitEthernet1/0/1
 switchport mode trunk
```

Some switch models have fixed 802.1Q encapsulation and reject `switchport trunk encapsulation dot1q`; enter that command only if the device supports selecting an encapsulation. Check with `show interfaces trunk` and `show vlan brief`.

## Router interface and router-on-a-stick examples

```text
interface Serial0/1/0
 ip address 10.10.10.6 255.255.255.252
 no shutdown
```

Set a serial clock rate only on the DCE end of a serial link, and only when the simulator/device requires it:

```text
interface Serial0/1/1
 clock rate 64000
```

Example router subinterface:

```text
interface GigabitEthernet0/0.80
 encapsulation dot1Q 80
 ip address 192.168.8.1 255.255.255.0
```

## DHCP example

```text
ip dhcp pool IT-DEPT
 network 192.168.8.0 255.255.255.0
 default-router 192.168.8.1
 dns-server <DNS_SERVER_IP>
```

Use the address of a real DNS service for `dns-server`; the default gateway is not automatically a DNS server.

## Routing examples

RIPv2 example for a `192.168.9.0/24` subnet. IOS RIP's `network` command uses the classful major network, so the statement is `192.168.0.0`:

```text
router rip
 version 2
 no auto-summary
 network 192.168.0.0
```

For IOS OSPF, the second value in a `network` statement is a wildcard mask, not a subnet mask:

```text
router ospf 10
 network 10.10.10.4 0.0.0.3 area 0
 network 192.168.2.0 0.0.0.255 area 0
```

## Port security example

Use port security on an edge access port, not on a trunk or switch-to-switch link:

```text
interface FastEthernet0/4
 switchport mode access
 switchport port-security
 switchport port-security maximum 1
 switchport port-security mac-address sticky
 switchport port-security violation shutdown
```

Save the configuration from privileged EXEC mode with `copy running-config startup-config`.
