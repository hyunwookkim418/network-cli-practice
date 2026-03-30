# Day 20 – DHCP Configuration (Router-Based)

Date: 2026-03-29

## Environment
- Cisco Packet Tracer
- Cisco Router (1941)

## Network Topology
```bash
PC (DHCP Client)
        |
   g0/0: 192.168.50.1
      Router (DHCP Server)
```

## CLI Commands
```bash
enable
configure terminal
interface g0/0
ip address 192.168.50.1 255.255.255.0
no shutdown
exit
ip dhcp excluded-address 192.168.50.1 192.168.50.10
ip dhcp pool OFFICE
network 192.168.50.0 255.255.255.0
default-router 192.168.50.1
end
write memory
```

## Key Concepts
- DHCP = Router automatically assigns IP addresses
- `excluded-address` = protects static IP range (gateway, servers, etc.)
- DHCP uses broadcast → works only within the same network
- The router itself acts as the DHCP server

## When to Use
- When setting up a new network (automatic IP assignment needed)
- In small to medium environments without a dedicated DHCP server
- In Data Center / Office LAN for fast deployment
- When you want to simplify IP management and avoid manual configuration

## Verification Commands
```bash
show ip dhcp binding
show ip dhcp pool
show running-config
```

## Troubleshooting Commands
```bash
debug ip dhcp server events
show ip interface brief
```
