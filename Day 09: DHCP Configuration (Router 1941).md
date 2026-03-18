# Day 09: DHCP Configuration (Router 1941)

Date: 2026-03-18

## Environment
- Cisco Packet Tracer
- Cisco Router (1941)

## Network Topology
```bash
PC (DHCP Client)
|
| 192.168.30.0/24
|
Router (g0/0: 192.168.30.1)
```

# Router Configuration
## CLI Commands
```bash
enable
configure terminal

interface g0/0
description LAN_Interface
ip address 192.168.30.1 255.255.255.0
no shutdown
exit

ip dhcp pool LAN_POOL
network 192.168.30.0 255.255.255.0
default-router 192.168.30.1
dns-server 8.8.8.8
exit

ip dhcp excluded-address 192.168.30.1 192.168.30.10

end
write memory
```

## Key Concept
- DHCP automatically assigns IP addresses to clients within a defined network range
- default-router defines the gateway for all clients
- excluded-address prevents IP conflicts for critical devices (gateway, servers, etc.)

## Verification Commands
```bash
show ip dhcp binding
show ip dhcp pool
show running-config
```
Troubleshooting Commands
show ip interface brief
debug ip dhcp server events
