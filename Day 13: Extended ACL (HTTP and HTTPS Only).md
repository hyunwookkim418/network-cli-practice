# Day 13: Extended ACL (HTTP and HTTPS Only)

Date: 2026-03-22

## Environment
- Cisco Packet Tracer
- Cisco Router (1941)

## Network Topology
```bash PC LAN (192.168.10.0/24)
        |
   Router
   g0/0: 192.168.10.1 (ACL 적용)
        |
        | Filtering (HTTP/HTTPS only)
        |
   g0/1: 203.0.113.10
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
no shutdown
exit
access-list 100 permit tcp 192.168.10.0 0.0.0.255 any eq 80
access-list 100 permit tcp 192.168.10.0 0.0.0.255 any eq 443
access-list 100 deny ip any any
interface g0/0
ip access-group 100 in
exit
interface g0/1
description WAN_Interface
ip address 203.0.113.10 255.255.255.0
no shutdown
exit
end
write memory
```

## Key Concept
- Extended ACL filters based on source, destination, protocol, and port
- Allows only HTTP (80) and HTTPS (443) traffic from LAN
- All other traffic is explicitly denied
- Applied inbound on LAN interface (g0/0)

## Verification Commands
- show access-lists
- show ip interface g0/0
- show running-config

## Troubleshooting Commands
- show access-lists
- show running-config interface g0/0
- debug ip packet
