Day41: Network CLI Practice

Date: 2026-04-18

30-Second Summary: Extended ACLs allow precise traffic control using source, destination, and port numbers. In this lab, I permitted HTTP and HTTPS traffic from a specific subnet and denied everything else. Applying the ACL inbound improves efficiency by filtering unwanted traffic early.

## Environment
- Cisco Router (Packet Tracer)

## CLI Commands
```bash
enable
configure terminal
access-list 100 permit tcp 192.168.10.0 0.0.0.255 any eq 80
access-list 100 permit tcp 192.168.10.0 0.0.0.255 any eq 443
access-list 100 deny ip any any
interface g0/0
ip access-group 100 in
no shutdown
exit
end
write memory
```

## Key Concepts
- Extended ACL filters traffic based on IP + protocol + port
- Applied inbound on interface to control traffic before routing decision

## Verification Commands
```bash
show access-lists
show ip interface g0/0
```

## Troubleshooting Commands
```bash
show running-config
show ip access-lists
```
