# Day 11: NAT Overload (PAT) Configuration

Date: 2026-03-20

## Environment
- Cisco Packet Tracer
- Cisco Router (1941)

## Network Topology
```bash
PC LAN (192.168.10.0/24)
        |
   Router
   g0/0: 192.168.10.1 (inside)
        |
        | NAT
        |
   g0/1: 203.0.113.10 (outside)
        |
     Internet
```

# Router Configuration
## CLI Commands
```bash
enable
configure terminal
interface g0/0
description LAN_Interface
ip address 192.168.10.1 255.255.255.0
ip nat inside
no shutdown
exit
interface g0/1
description WAN_Interface
ip address 203.0.113.10 255.255.255.0
ip nat outside
no shutdown
exit
access-list 1 permit 192.168.10.0 0.0.0.255
ip nat inside source list 1 interface g0/1 overload
end
write memory
```

## Key Concept
- NAT Overload (PAT) allows multiple internal private IP addresses to share a single public IP address using port translation.
- ip nat inside and ip nat outside define traffic direction for NAT processing.
- The ACL specifies which internal networks are eligible for translation.
- The overload keyword enables port-based translation (PAT).

## Verification Commands
```bash
show ip nat translations
show ip nat statistics
show ip interface brief
show running-config
```

## Troubleshooting Commands
```bash
show access-lists
show ip nat translations verbose
debug ip nat
show running-config interface g0/0
show running-config interface g0/1
```
