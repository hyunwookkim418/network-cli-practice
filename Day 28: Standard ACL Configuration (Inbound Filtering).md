# Day 28: Standard ACL Configuration (Inbound Filtering)

Date: 2026-04-05

## Environment
- Cisco Packet Tracer
- Cisco Router

## Network Topology
```bash
PC LAN (192.168.10.0/24)
        |
     Router (g0/0)
```

## CLI Commands
```bash
enable
configure terminal
access-list 10 permit 192.168.10.0 0.0.0.255
access-list 10 deny any
interface g0/0
description LAN_Interface
ip address 192.168.10.1 255.255.255.0
ip access-group 10 in
no shutdown
exit
end
write memory
```

## Key Concepts
- Standard ACL filters traffic based only on source IP address
- ACL should be placed close to the destination for better control

## Verification Commands
```bash
show access-lists
show ip interface g0/0
```

## Troubleshooting Commands
```bash
show running-config
debug ip packet
```

## When to Use
- When you need to control which source networks are allowed or denied
- Basic traffic filtering without needing destination or port-level control
- Small or simple network environments
