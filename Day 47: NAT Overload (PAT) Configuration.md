# Day 47: NAT Overload (PAT) Configuration

Date: 2026-04-24

30-Second Summary: NAT overload, also known as PAT, allows multiple internal hosts to access the internet using a single public IP address by assigning unique port numbers. Inside interfaces are marked with ip nat inside, and the outside interface with ip nat outside. Traffic matching the ACL is translated using the public IP of the outside interface.

## Environment
- Cisco Router (Packet Tracer / Lab)
- Inside Network: 192.168.10.0/24
- Outside (ISP): 203.0.113.0/30

## CLI Configuration
```
enable
configure terminal
interface g0/0
description LAN_INSIDE
ip address 192.168.10.1 255.255.255.0
ip nat inside
no shutdown
exit
interface g0/1
description ISP_OUTSIDE
ip address 203.0.113.2 255.255.255.252
ip nat outside
no shutdown
exit
access-list 1 permit 192.168.10.0 0.0.0.255
ip nat inside source list 1 interface g0/1 overload
end
write memory
```

## Key Concept
- NAT Overload (PAT) allows multiple internal devices to share a single public IP using different port numbers
- `overload` keyword enables port-based translation (many-to-one NAT)

## Verification Commands
```
show ip nat translations
show ip nat statistics
```

## Troubleshooting Commands
```
show access-lists
show ip interface brief
```
