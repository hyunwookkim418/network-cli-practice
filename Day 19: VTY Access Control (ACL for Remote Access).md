# Day 19: VTY Access Control (ACL for Remote Access)

Date: 2026-03-28

## Environment
- Cisco Packet Tracer
- Cisco Router

## Network Topology
```bash
PC (192.168.40.0/24)
        |
   Router (g0/0: 192.168.40.1)
```

# Router Configuration
## CLI Commands
```bash
enable
configure terminal
interface g0/0
description LAN_Interface
ip address 192.168.40.1 255.255.255.0
no shutdown
exit
access-list 10 permit 192.168.40.0 0.0.0.255
access-list 10 deny any
line vty 0 4
access-class 10 in
end
write memory
```

## Key Concepts
- ACL (Access Control List) is used to control remote access to the router
- ACL 10 allows only the 192.168.40.0/24 network
- `access-class` applies the ACL to VTY (remote access lines)
- Only devices in the permitted network can access via Telnet/SSH
- Interface g0/0 defines the network where allowed hosts exist

## When to Use
- Restrict remote access (Telnet/SSH) to network devices
- Allow only specific subnets (e.g., internal LAN) to manage routers
- Block unauthorized external access to VTY lines
- Apply basic security control before implementing full AAA
- Used in small networks or initial device hardening

## Verification Commands
```bash
show access-lists
show running-config
show line vty 0 4
```

## Troubleshooting Commands
```bash
show ip interface brief
show users
debug ip packet
```
