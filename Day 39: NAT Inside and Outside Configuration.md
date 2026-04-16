# Day 39 – NAT Inside and Outside Configuration

Date: April 16, 2026

## Environment
- Cisco Packet Tracer
- Router (ISR)

## CLI Configuration
```bash
enable
configure terminal
interface g0/0
ip nat inside
ip address 192.168.50.1 255.255.255.0
no shutdown
exit
interface g0/1
ip nat outside
ip address 203.0.113.2 255.255.255.252
no shutdown
end
write memory
```

## Key Concepts
- `ip nat inside` and `ip nat outside` define traffic direction for NAT translation
- Inside network = private IP space, Outside = public/WAN interface

## Verification Commands

```bash
show ip interface brief
show running-config
```

## Troubleshooting Commands

```bash
show ip nat translations
show ip nat statistics
```
