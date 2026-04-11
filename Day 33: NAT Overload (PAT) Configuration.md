# Day 33: NAT Overload (PAT) Configuration

Date: 2026-04-10

30-Second Summary: NAT overload (PAT) allows multiple internal devices to share a single public IP address by using different port numbers. Inside interfaces are marked with `ip nat inside` and the outside interface with `ip nat outside`. The command `ip nat inside source list 1 interface g0/1 overload` translates all permitted internal IPs to the public IP of g0/1.

## Environment
- Cisco Packet Tracer
- Cisco Router

## CLI Commands
```bash
enable
configure terminal
interface g0/0
description LAN_Interface
ip address 192.168.30.1 255.255.255.0
ip nat inside
no shutdown
exit
interface g0/1
description WAN_Interface
ip address 198.51.100.2 255.255.255.0
ip nat outside
no shutdown
exit
access-list 1 permit 192.168.30.0 0.0.0.255
ip nat inside source list 1 interface g0/1 overload
end
write memory
```

## Key Concepts
- NAT Overload = Many private IPs → One public IP using port translation
- Access-list defines which internal IPs are allowed for NAT

## Verification Commands
```bash
show ip nat translations
show ip nat statistics
```

## Troubleshooting Commands
```bash
show access-lists
show ip interface brief
```
