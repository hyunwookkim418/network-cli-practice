# Day 18: STP Root Bridge Configuration (Per VLAN)

Date: 2026-03-27

## Environment
- Cisco Packet Tracer
- Cisco Switch (2960)

## Network Topology
```bash
        Core Switch (Root)
             |
        -------------
        |           |
   Access SW1   Access SW2
```

## CLI Commands
```bash
enable
configure terminal
spanning-tree vlan 10 root primary
spanning-tree vlan 20 root primary
interface g0/1
description Uplink_to_Access_Switch
switchport mode trunk
switchport trunk allowed vlan 10,20
no shutdown
end
write memory
```

## Key Concepts
- STP runs per VLAN (PVST+)
- Each VLAN elects its own Root Bridge
- `root primary` forces this switch to become Root
- Without configuration → Root is selected based on lowest MAC (unpredictable)
- Best practice: Core/Distribution switch should be Root

## When to Use
- Initial network design
- Core / Distribution layer setup
- When STP path is not optimal
- When Access switch becomes Root (must fix)

## Verification Commands
```bash
show spanning-tree vlan 10
show spanning-tree vlan 20
```
## Troubleshooting Commands
```bash
show spanning-tree
show spanning-tree root
show spanning-tree interface g0/1
```
