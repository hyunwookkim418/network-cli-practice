# Day 37: Trunk Configuration & STP Root Optimization

30-Second Summary: Trunk links allow multiple VLANs to travel across a single interface using 802.1Q tagging. In this lab, I configured a static trunk and disabled DTP for stability and security. I also optimized STP by assigning this switch as the primary root for VLAN 10 and secondary root for VLAN 20, improving traffic distribution and ensuring redundancy.

Date: April 14, 2026

## Environment
- Cisco Switch (Packet Tracer / Lab)
- VLANs: 10, 20, 30

## CLI Configuration
```bash
enable
configure terminal
interface g0/1
switchport mode trunk
switchport trunk allowed vlan 10,20,30
switchport nonegotiate
no shutdown
exit
spanning-tree vlan 10 root primary
spanning-tree vlan 20 root secondary
end
write memory
```

## Key Concepts
- Static Trunk Configuration: Using switchport mode trunk with nonegotiate disables DTP and ensures a stable, manual trunk setup.
- STP Root Control per VLAN: Assigning primary and secondary roots helps optimize traffic flow and provides failover capability.

## Verification Commands
```bash
show interfaces trunk
show spanning-tree vlan 10
show spanning-tree vlan 20
```

## Troubleshooting Commands
```bash
show running-config interface g0/1
show spanning-tree summary
```
