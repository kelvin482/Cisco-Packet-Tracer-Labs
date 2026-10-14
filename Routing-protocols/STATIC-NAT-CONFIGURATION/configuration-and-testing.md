# Static NAT Configuration and Testing

## 1. What Is Static NAT?

Static Network Address Translation (Static NAT) maps one internal IP address to one fixed external IP address.

It is commonly used when an internal device, such as a server, requires a consistent address mapping for communication with external networks.

**Key concept:** Static NAT provides a permanent one-to-one mapping between an inside local address and an inside global address.

## 2. OSPF Configuration

Open Shortest Path First (OSPF) is a dynamic routing protocol that allows routers to exchange routing information and learn paths to remote networks.

### Basic Cisco IOS Example

```cisco
enable
configure terminal

router ospf 1
 network 192.168.1.0 0.0.0.255 area 0
 network 10.0.0.0 0.255.255.255 area 0

end
```

**Explanation:**
- `router ospf 1` — starts OSPF process 1.
- `network` — identifies interfaces that participate in OSPF and the networks to advertise.
- `area 0` — assigns the matching interfaces to OSPF area 0.
- `end` — exits configuration mode.

*Use the actual network addresses and wildcard masks from your topology.*

## 3. Static NAT Configuration

### Basic Cisco IOS Example

```cisco
configure terminal

ip nat inside source static 192.168.1.10 203.0.113.10

interface gigabitEthernet 0/0
 ip nat inside
 exit

interface gigabitEthernet 0/1
 ip nat outside
 exit

end
```

**Explanation:**
- `ip nat inside source static` — creates a fixed one-to-one address mapping.
- `ip nat inside` — identifies the interface facing the internal network.
- `ip nat outside` — identifies the interface facing the external network.

In this example, the internal address `192.168.1.10` maps to `203.0.113.10`. These are example addresses, not necessarily the addresses used in the actual lab.

## 4. Testing the NAT Configuration

After configuring NAT, generate traffic and verify the results.

```cisco
show ip nat translations
show ip nat statistics
show ip route
show ip interface brief
```

Test connectivity using:

```cisco
ping <server-ip>
traceroute <server-ip>
```

**What to check:**
- Interfaces are operational.
- Routes to the destination and return network are available.
- The expected Static NAT mapping is configured.
- NAT counters or translation information change when applicable traffic passes through the router.
- Ping and traceroute results are recorded for comparison.

A configured static mapping may appear in the translation table even before traffic is generated. Therefore, verify both the mapping and the actual traffic behavior.

## 5. Before-and-After Testing

| Test | Before NAT | After NAT |
|---|---|---|
| IP connectivity | Record results | Repeat test |
| Traceroute | Record packet path | Compare packet path |
| NAT mapping | Inspect table | Verify configured mapping |
| NAT statistics | Record baseline | Check for traffic and translation activity |


This exercise demonstrates how OSPF provides dynamic routing while Static NAT provides a fixed one-to-one IP address mapping. Connectivity tests and NAT verification commands help determine whether the network is configured and operating as intended.