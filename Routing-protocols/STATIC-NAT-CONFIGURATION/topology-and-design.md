# Network Topology and Design Explanation

## 1. Understanding the Topology

The topology represents a routed network consisting of internal hosts, routers, an external network, and a Google test server used to test connectivity.

Each component has a specific responsibility:

- **Hosts:** Generate traffic and act as communication endpoints.
- **Routers:** Forward packets between different IP networks.
- **OSPF:** Allows participating routers to exchange routing information.
- **NAT router:** Translates IP addresses according to the configured NAT rules.
- **External test server:** Provides a destination for connectivity testing.

The topology should label device names, interface names, IP addresses, and network segments to make packet movement easy to understand.

## 2. Why Do We Configure OSPF?

OSPF is configured to allow routers to learn routes to networks that are not directly connected to them.

Without a valid route, a router may not know where to forward packets destined for a remote network.

OSPF helps to:

- Exchange routing information between participating routers.
- Discover reachable remote networks.
- Select paths based on routing metrics.
- Update routing information when network conditions change.

**Important:** OSPF handles routing; it does not translate IP addresses.

## 3. Why Do We Configure Static NAT?

Static NAT is configured to establish a fixed mapping between an internal IP address and an external IP address.

This is useful when a device needs a consistent translated address.

Static NAT helps to:

- Map an inside local address to an inside global address.
- Provide consistent address translation.
- Support communication involving translated addresses when routing and security policies permit it.

NAT does not automatically create routes, permit blocked traffic, or guarantee successful communication.

## 4. Understanding NAT Inside and Outside

The NAT router must identify which interface faces the internal network and which faces the external network.

- **Inside interface:** Faces the network containing the device whose address is translated.
- **Outside interface:** Faces the external network.

Correct interface assignment ensures that the router applies NAT in the intended direction.

## 5. Important Verification Commands

| Command | Purpose |
|---|---|
| `show ip interface brief` | Checks interface IP addresses and status. |
| `show ip route` | Displays known routes. |
| `show ip ospf neighbor` | Checks OSPF neighbor relationships. |
| `show ip protocols` | Displays routing protocol information. |
| `ping <destination-ip>` | Tests destination reachability. |
| `traceroute <destination-ip>` | Examines the Layer 3 path to a destination. |
| `show ip nat translations` | Displays NAT translation entries. |
| `show ip nat statistics` | Displays NAT statistics. |
| `show running-config` | Displays the active configuration. |

These are common Cisco IOS commands. Use the corresponding ASA commands if the lab runs on Cisco ASA.

## 6. How We Tested the Network

Testing was performed in two stages.

### Before NAT
1. Verified interface status and IP addressing.
2. Checked OSPF routing and route availability.
3. Pinged the external test server.
4. Ran traceroute to examine the packet path.
5. Inspected the NAT translation table.

### After NAT
1. Configured the fixed address mapping.
2. Assigned the NAT inside and outside interfaces.
3. Repeated ping and traceroute.
4. Inspected the NAT translation table and statistics.
5. Compared the results and documented any issues.

## 7. Key Lessons

- Routing determines where packets are forwarded.
- NAT translates addresses according to configured rules.
- OSPF and Static NAT perform different functions.
- Correct routing, return paths, and security policies are necessary for successful communication.
- Testing before and after configuration provides evidence of the changes made.
