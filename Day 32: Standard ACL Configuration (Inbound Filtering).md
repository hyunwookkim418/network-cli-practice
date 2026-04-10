# Day 32: Standard ACL Configuration (Inbound Filtering)

Date: 2026-04-09

30-Second Summary: A Standard ACL filters traffic based only on the source IP address. It is typically applied close to the destination to avoid unintentionally blocking other traffic. In this lab, I permitted the 192.168.10.0 network and denied all other traffic, then applied the ACL inbound on an interface to control access.

## Environment
- Cisco Packet Tracer
- Cisco Router

## CLI Configuration
```bash
enable
configure terminal
access-list 10 permit 192.168.10.0 0.0.0.255
access-list 10 deny any
interface g0/0
ip access-group 10 in
exit
interface g0/1
ip address 203.0.113.1 255.255.255.0
no shutdown
end
write memory
```

## Key Concepts
- Standard ACL = Filters source IP only
- Implicit deny any exists at the end → must explicitly permit required traffic

## Verification Commands
```bash
show access-lists
show ip interface g0/0
```

## Troubleshooting
```bash
show running-config
debug ip packet
```

## When to Use
- Basic traffic control based on source network
- Small to mid-size environments with simple policies
