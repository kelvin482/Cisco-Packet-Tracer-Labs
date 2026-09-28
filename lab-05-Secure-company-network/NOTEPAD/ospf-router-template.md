# IOS OSPF Router Template

This is a template for an IOS router, not an ASA. IOS OSPF `network` statements use wildcard masks. Replace the example router ID and networks with the confirmed interfaces on the target router.

```text
configure terminal
router ospf 35
 router-id <UNIQUE_ROUTER_ID>
 network <NETWORK_ADDRESS> <WILDCARD_MASK> area 0
end
```

The original scratch note records router ID `1.1.4.4` and these link networks:

```text
network 30.30.30.0 0.0.0.3 area 0
network 197.200.100.0 0.0.0.3 area 0
network 197.200.100.4 0.0.0.3 area 0
```

Those addresses are retained only as historical scratch values; the 197.200.100.x entries conflict with the current ISP2 addressing-plan image and are not confirmed for the current project. Do not paste them until the router's links are verified. OSPF router IDs must be unique within the OSPF routing domain.
