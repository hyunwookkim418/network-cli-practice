# Day 34: DHCP Server Configuration

Date: 2026-04-11

30-Second Summary: DHCP allows a router to automatically assign IP addresses to clients, reducing manual configuration and human error. By defining a DHCP pool, the router dynamically distributes IP, gateway, and DNS information to devices in the network. This is essential in real environments where hundreds of devices need consistent and efficient IP management.

## Environment
- Cisco Packet Tracer
- Cisco Router

## CLI Commands
```bash
enable
configure terminal
interface g0/0
description LAN_Interface
ip address 192.168.50.1 255.255.255.0
no shutdown
exit
ip dhcp excluded-address 192.168.50.1 192.168.50.20
ip dhcp pool OFFICE_POOL
network 192.168.50.0 255.255.255.0
default-router 192.168.50.1
dns-server 8.8.8.8
end
write memory
```

## Key Concepts
- DHCP automates IP assignment → reduces admin overhead and misconfiguration
- Excluded addresses prevent conflicts with statically assigned devices (servers, printers, etc.)

## Verification Commands
```bash
show ip dhcp binding
show ip dhcp pool
```

## Troubleshooting Commands
```bash
show running-config | section dhcp
show ip interface brief
```

## When to Use
- Office environments with many user devices
- Networks where manual IP management is inefficient
- Situations requiring quick deployment and scalability
