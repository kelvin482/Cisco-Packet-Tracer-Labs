# ASA Network Object NAT (PAT)

Network object NAT defines a source network and a translation. Dynamic PAT using `interface` translates hosts to the address of the selected egress interface, allowing many inside hosts to share that interface address.

The syntax in the original notes is ASA object NAT syntax:

```text
object network LAN-OUTSIDE1
 subnet 172.16.0.0 255.255.0.0
 nat (INSIDE1,OUTSIDE1) dynamic interface
```

Other Lab 5 source networks supplied for this project are WLAN `10.20.0.0/16` and DMZ `10.11.11.0/27`. Create NAT only for traffic that should be translated and for the actual interface path used by the ASA. The object name is descriptive; interface names must match `nameif` values on the device.

The old notes contain several overlapping objects and interface pairs. Do not paste every mapping without confirming the physical/logical topology, routing, and intended failover behavior. Verify translations with `show nat` and `show xlate` if supported by the Packet Tracer ASA model.

Reference: [Cisco ASA 9.12 Network Address Translation](https://www.cisco.com/c/en/us/td/docs/security/asa/asa912/configuration/firewall/asa-912-firewall-config/nat-basics.html).
