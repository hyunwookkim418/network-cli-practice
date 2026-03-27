# Day 17: STP Root Bridge Control

Date: 2026-03-26

## Environment
- Cisco Packet Tracer
- Cisco Switch (2960)

## Network Topology
```bash
Core Switch (Root)
|
Access Switch
```

## CLI Commands
```bash
enable
configure terminal
spanning-tree vlan 10 root primary
interface g0/1
switchport mode trunk
switchport trunk allowed vlan 10,20,30
no shutdown
end
write memory
```

## Key Concepts
- Root Bridge = The central switch used as the reference point in STP
- Default → Selected based on lowest MAC address (can be inefficient)
- `root primary` → Forces this switch to become the Root Bridge
- Best practice: Set the Core switch as the Root Bridge

## When to Use
- During initial network deployment (design phase)
- When configuring Core / Distribution switches
- When you need to control traffic flow intentionally
- When STP paths are not optimal
- If the Root is on an Access switch, it must be corrected immediately

## Verification Commands
```bash
show spanning-tree vlan 10
show spanning-tree root
```
