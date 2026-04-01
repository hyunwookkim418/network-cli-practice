# Day 22: Static Route & Default Route Configuration

Date: 2026-03-31

## Environment
- Cisco Packet Tracer
- Cisco Router

## Network Topology
```bash
PC LAN (192.168.60.0/24)
        |
   Router
   g0/0: 192.168.60.1
        |
   -------------------------
   |                       |
192.168.60.2         192.168.60.254
(Internal Router)     (ISP / Gateway)
```

## CLI Commands
```bash
enable
configure terminal
interface g0/0
description LAN_Interface
ip address 192.168.60.1 255.255.255.0
no shutdown
exit
ip route 0.0.0.0 0.0.0.0 192.168.60.254
ip route 10.10.10.0 255.255.255.0 192.168.60.2
end
write memory
```

## Key Concepts
- Static Route = Manually defines a path to a specific network
- Default Route = Sends all unknown traffic to a single next-hop

## When to Use
- Small networks (no need for dynamic routing protocols)
- When precise path control is required
- Internet connectivity (Default Route is essential)

## Verification Commands
```bash
show ip route
show running-config
```

## Troubleshooting Commands
```bash
ping 192.168.60.254
ping 10.10.10.1
traceroute 10.10.10.1
```
