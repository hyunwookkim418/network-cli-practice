# Day 12: Standard ACL Configuration (Router 1941)

Date: 2026-03-22

## Environment
- Cisco Packet Tracer
- Cisco Router (1941)

## Network Topology
```bash
PC LAN (192.168.10.0/24)
        |
   Router
   g0/0: 192.168.10.1 (ACL 적용)
        |
        | Filtering
        |
   g0/1: 10.0.0.1
        |
     WAN
```

# Router Configuration
## CLI Commands
```bash enable
configure terminal
access-list 10 permit 192.168.10.0 0.0.0.255
access-list 10 deny any
interface g0/0
description LAN_Interface
ip address 192.168.10.1 255.255.255.0
ip access-group 10 in
no shutdown
exit
interface g0/1
description WAN_Interface
ip address 10.0.0.1 255.255.255.252
no shutdown
exit
end
write memory
```

## Key Concept
- Standard ACL filters traffic based on source IP only
- ACL is applied using ip access-group on an interface
- Direction matters → in means traffic entering the interface
- Implicit deny exists → all unmatched traffic is blocked

## Verification Commands
- show access-lists
- show ip interface g0/0
- show running-config

## Troubleshooting Commands
- show access-lists
- show running-config interface g0/0
- debug ip packet
