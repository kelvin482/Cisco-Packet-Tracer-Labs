# Secure Switch Management with SSH

SSH encrypts remote management sessions. The original note used the same simple password for several accounts; this cleaned example uses placeholders and avoids publishing credentials.

```text
configure terminal
hostname CORE-SW2
no ip domain-lookup
ip domain-name <LAB_DOMAIN>
username <ADMIN_USER> privilege 15 secret <STRONG_UNIQUE_SECRET>
enable secret <STRONG_ENABLE_SECRET>
crypto key generate rsa modulus 2048
ip ssh version 2
ip access-list standard SSH-ADMIN
 permit host <AUTHORIZED_ADMIN_PC_IP>
 deny any
line vty 0 15
 login local
 transport input ssh
 access-class SSH-ADMIN in
end
copy running-config startup-config
```

The lab requirements say SSH access should be limited to the Senior Network Security Engineer PC. Use that PC's verified address in `<AUTHORIZED_ADMIN_PC_IP>`; permitting the entire management subnet would be broader than that requirement. Confirm the device model supports the RSA key size shown; use a supported size if Packet Tracer's simulated IOS is more limited.

The original console and local usernames/passwords were literal `cisco` values. They have been removed from the published example. Never commit real or reused credentials.

Verify using `show ip ssh`, `show access-lists`, and an SSH client from the authorized PC.
