# Configure the ASA Outside Interface

An ASA interface needs an IP address, a name, and a security level before it can serve as a named firewall zone. The lab transcript documents `GigabitEthernet1/1` as `OUTSIDE1` with `105.100.50.2/30`.

```text
configure terminal
interface GigabitEthernet1/1
 nameif OUTSIDE1
 security-level 0
 ip address 105.100.50.2 255.255.255.252
 no shutdown
```

Security level 0 is appropriate for the outside zone in this lab's design. Configure other ASA interfaces only from their confirmed addressing and intended roles; do not copy the outside settings to inside or DMZ interfaces.

Verify with `show interface ip brief` or the equivalent supported by the Packet Tracer ASA model, and `show running-config interface GigabitEthernet1/1`.
