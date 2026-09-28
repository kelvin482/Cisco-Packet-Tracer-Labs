# Spanning Tree Protection on Edge Ports

PortFast lets an end-device access port move to forwarding without the normal spanning-tree delay. BPDU Guard err-disables the port if it receives a spanning-tree BPDU, helping protect the topology from an incorrectly connected switch.

Use these commands only on ports connected to end devices. Do not apply PortFast or BPDU Guard indiscriminately to switch-to-switch trunks.

```text
configure terminal
interface range <EDGE_ACCESS_PORTS>
 spanning-tree portfast
 spanning-tree bpduguard enable
end
copy running-config startup-config
```

The original note applied the settings to `FastEthernet0/1-24`, which may include uplinks or trunks. Replace the placeholder with the verified edge access ports for that specific switch. Check port roles with `show interfaces status` and `show interfaces trunk`.
