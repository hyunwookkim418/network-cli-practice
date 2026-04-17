# Day 40: VLAN & Trunk Configuration

Date: 2026-04-17

30-Second Summary: VLANs segment the network at Layer 2 to improve security and reduce broadcast traffic. Access ports are assigned to a single VLAN for end devices, while trunk ports carry multiple VLANs between switches using tagging. Proper VLAN and trunk configuration ensures different departments can communicate across switches without mixing traffic.

## CLI Commands
```bash
enable
configure terminal
vlan 10
name SALES
vlan 20
name HR
exit
interface range g0/1 - 2
switchport mode access
switchport access vlan 10
spanning-tree portfast
no shutdown
exit
interface f0/1
switchport mode trunk
switchport trunk allowed vlan 10,20
no shutdown
end
write memory
```

## Key Concepts
- VLAN = Logical segmentation (Layer 2)
- Trunk = Multiple VLANs over one link (802.1Q)

## Verification Commands
```bash
show vlan brief
show interfaces trunk
```

## Troubleshooting Commands
```bash
show interfaces status
show running-config interface f0/1
```
