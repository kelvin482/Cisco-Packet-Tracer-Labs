# ASA Static Routes and OSPF

Static routes and OSPF serve different routing needs in this design. A static default route can send Internet-bound traffic toward an ISP. OSPF can exchange internal routes between the ASA and Layer 3 switches. OSPF is useful when internal routes change or there are multiple paths; static routes are simple and explicit for fixed destinations.

## Static default route examples

The saved notes show the ISP1 link as `105.100.50.0/30`, with ASA address `.2` and ISP next hop `.1`. This command is consistent with that link:

```text
route OUTSIDE1 0.0.0.0 0.0.0.0 105.100.50.1
```

The scratch transcript shows an administrative distance of 70 for a second, less-preferred default route, but the ISP2 subnet/next hop conflicts with the addressing-plan image. Do not paste a guessed next hop:

```text
route OUTSIDE2 0.0.0.0 0.0.0.0 <ISP2_NEXT_HOP> 70
```

Replace the placeholder only after checking the ISP2 link in the current `.pkt` file. A higher administrative distance makes this route less preferred than the default-distance route when both are available.

## OSPF example from the ASA transcript

ASA OSPF `network` statements use a subnet mask, unlike IOS OSPF statements, which use wildcard masks. The transcript shows process 35 and router ID `1.1.8.8`:

```text
router ospf 35
 router-id 1.1.8.8
 network 105.100.50.0 255.255.255.252 area 0
 network 10.2.2.8 255.255.255.252 area 0
 network 10.2.2.12 255.255.255.252 area 0
 network 10.11.11.0 255.255.255.224 area 0
```

These are cleaned from the saved ASA CLI transcript. Confirm that each network matches an interface on this ASA before applying. The ISP2 OSPF network in the original transcript conflicts with the addressing-plan image, so it is intentionally omitted pending verification.

Check routes with `show route`, and OSPF state with the ASA's supported OSPF show commands. Exact command support can vary by Packet Tracer ASA model/version.

Reference: [Cisco ASA 9.12 OSPF Configuration](https://www.cisco.com/c/en/us/td/docs/security/asa/asa912/configuration/general/asa-912-general-config/route-ospf.html).
