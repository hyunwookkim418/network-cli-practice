# Day 36: DHCP Server Configuration

Date: 2026-04-13

30-Second Summary: I configured a Cisco router as a DHCP server to automatically assign IP addresses to clients in the LAN. I excluded a specific IP range for static devices and defined the default gateway and DNS settings. This reduces manual IP configuration and improves network scalability.

## Environment
- Cisco Router
- Cisco Packet Tracer

## CLI Commands
```bash
enable
configure terminal
interface g0/0
ip address 192.168.100.1 255.255.255.0
no shutdown
exit
ip dhcp excluded-address 192.168.100.1 192.168.100.10
ip dhcp pool LAN_POOL
network 192.168.100.0 255.255.255.0
default-router 192.168.100.1
dns-server 8.8.8.8
end
write memory
```

## Key Concepts
- DHCP automatically assigns IP addresses, reducing manual configuration effort
- Excluded addresses are reserved for static devices like servers, printers, or gateways

## Verification Commands
```bash
show ip dhcp binding
show ip dhcp pool
show ip interface brief
```

## Troubleshooting
```bash
debug ip dhcp server events
show running-config | section dhcp
```

## When to Use
- Small to medium networks where centralized IP management is needed
- Environments where manual IP assignment is inefficient or error-prone
