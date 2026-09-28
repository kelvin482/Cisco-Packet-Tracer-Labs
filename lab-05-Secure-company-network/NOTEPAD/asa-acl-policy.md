# ASA Access Control Policy Review

An ASA access control list (ACL) permits or denies traffic on an interface. The rules should name the intended source, destination, protocol, and service. A syntactically valid ACL can still expose more hosts or services than intended.

The original `RES` ACL permits ICMP, HTTP, and DNS from `any` to `any`, then applies that same broad rule set on outside and DMZ interfaces. This does not express a least-privilege policy and should not be treated as a final firewall policy without confirming the lab's intended traffic.

The original note also has `ss-list`; the ASA command is `access-list`.

Use a policy-specific ACL name and confirmed objects/hosts. This is a structure example only; replace the placeholders with approved lab endpoints and services:

```text
access-list OUTSIDE1-IN extended permit tcp any object <DMZ_WEB_SERVER> eq 80
access-group OUTSIDE1-IN in interface OUTSIDE1
```

Create separate rules for each required service and interface. Do not add a broad `permit ip any any` rule as a shortcut. Verify policy behavior in Packet Tracer with the intended traffic tests and inspect counters with the supported `show access-list` command.

Reference: [Cisco ASA 9.12 Access Control Lists](https://www.cisco.com/c/en/us/td/docs/security/asa/asa912/configuration/firewall/asa-912-firewall-config/access-acls.html).
