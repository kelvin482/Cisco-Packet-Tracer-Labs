# ASA ACL Command Examples

This note separates ACL syntax from the policy decision. The commands below preserve the services recorded in the original notes—ICMP, HTTP, and DNS—but the original `any any` scope is broad. Use them only if that broad reach is an intentional lab requirement.

```text
access-list RES extended permit icmp any any
access-list RES extended permit tcp any any eq 80
access-list RES extended permit tcp any any eq 53
access-list RES extended permit udp any any eq 53
```

The corresponding application syntax from the scratch notes is:

```text
access-group RES in interface OUTSIDE1
access-group RES in interface OUTSIDE2
```

Confirm that the ACL should be attached to both interfaces and that the same policy is appropriate on each. ASA ACLs are ordered; the first matching rule is applied, and traffic not permitted by an ACL is denied. Replace `any` values with the actual source and destination objects/hosts when narrowing the policy.

The phrase 'inspection policy' is not accurate for these lines: they are access-list rules. ASA protocol inspection is configured separately through a class map, policy map, and service policy.

Reference: [Cisco ASA 9.12 Access Control Lists](https://www.cisco.com/c/en/us/td/docs/security/asa/asa912/configuration/firewall/asa-912-firewall-config/access-acls.html).
