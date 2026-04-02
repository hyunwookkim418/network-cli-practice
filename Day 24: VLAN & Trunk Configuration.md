# Day 24: VLAN & Trunk Configuration

Date: 2026-04-02

## Environment
- Cisco Packet Tracer
- Cisco Switch (2960)

## Network Topology
```bash
PC (VLAN 30)
     |
   g0/1
   Switch
   g0/24 (Trunk)
     |
   Another Switch / Router
```

## CLI Commands
```bash
enable
configure terminal
vlan 30
name ENGINEERING
interface g0/1
switchport mode access
switchport access vlan 30
spanning-tree portfast
no shutdown
exit
interface g0/24
switchport mode trunk
switchport trunk allowed vlan 10,20,30
no shutdown
end
write memory
```

## Key Concepts
- Access Port → Assigns a device to a single VLAN (end devices like PC)
- Trunk Port → Carries multiple VLANs between switches or to routers

## When to Use
- When separating departments (e.g., Engineering, Sales, HR)
- When connecting multiple switches with VLAN traffic
- When implementing scalable Layer 2 network design

## Verification Commands
```bash
show vlan brief
show interfaces trunk
```

## Troubleshooting Commands
```bash
show running-config
show interfaces status
```
