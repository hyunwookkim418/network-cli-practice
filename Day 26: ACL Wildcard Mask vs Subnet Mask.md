# Day 26: ACL Wildcard Mask vs Subnet Mask

Date: 2026-04-03

## Environment
- Cisco Packet Tracer
- Cisco Router

## CLI Commands
```bash
enable
configure terminal
interface g0/0
description LAN_Interface
ip address 192.168.70.1 255.255.255.0
no shutdown
exit
access-list 10 permit 192.168.70.0 0.0.0.255
interface g0/1
ip access-group 10 out
no shutdown
end
write memory
```

## Key Concepts
## Subnet Mask (Used in IP Addressing)
- Defines the network structure
- Identifies which portion is network vs host
- Example:
```bash
255.255.255.0 = /24 network
```

## Wildcard Mask (Used in ACL)
- Defines matching rules for traffic
- Opposite logic of subnet mask:
```bash
0 = must match  
1 = ignore
```
- Example:
```bash
0.0.0.255 → match entire 192.168.70.0/24 network
```

## Why Wildcard Mask?
- ACLs require flexibility:
```bash
access-list 10 permit 192.168.70.10 0.0.0.0
→ Match single IP
```
```bash
access-list 10 permit 192.168.0.0 0.0.255.255
→ Match multiple subnets
```

## Verification Commands
```bash
show access-lists
show ip interface brief
show running-config
```

## Troubleshooting Commands
```bash
show access-lists
show ip interface g0/1
debug ip packet
```
