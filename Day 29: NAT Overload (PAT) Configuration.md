# Day 29: NAT Overload (PAT) Configuration

Date: 2026-04-06

## 30-Second Summary
- I configured NAT overload, or PAT, so multiple internal devices can share one public IP. I set inside and outside interfaces, defined an ACL, and used `ip nat inside source list 1 interface g0/1 overload` to translate private IPs to the g0/1 address using ports.

## Environment
- Cisco Packet Tracer
- Cisco Router

## Network Topology
```bash
LAN (192.168.70.0/24)
        |
     Router
 g0/0 (Inside)
 g0/1 (Outside - Public IP)
        |
      Internet
```

## CLI Commands
```bash
enable
configure terminal

interface g0/0
description LAN_Interface
ip address 192.168.70.1 255.255.255.0
ip nat inside
no shutdown
exit

interface g0/1
description WAN_Interface
ip address 203.0.113.10 255.255.255.0
ip nat outside
no shutdown
exit

access-list 1 permit 192.168.70.0 0.0.0.255
ip nat inside source list 1 interface g0/1 overload

end
write memory
```

## Key Concepts
- NAT Overload (PAT) = many private IPs → one public IP (using ports)
- ACL defines which internal IPs are translated

## Verification Commands
```bash
show ip nat translations
show ip nat statistics
```

## Troubleshooting Commands
```bash
show ip interface brief
show access-lists
```

## When to Use
- When public IP addresses are limited
- For internet access in most enterprise networks
- Standard design for internal users accessing external networks
