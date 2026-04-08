# Day 30: VLAN & Trunk Configuration

Date: 2026-04-07

Summary: VLANs segment a network at Layer 2 to improve security and reduce broadcast traffic. Devices in different VLANs cannot communicate by default, so trunk links carry multiple VLANs using 802.1Q. This enables scalable network design. The main risk is misconfiguration, like missing VLANs on a trunk. In my experience, I used VLANs and trunks to separate departments while maintaining connectivity across switches.

## Environment
- Cisco Packet Tracer
- Cisco Switch (2960)

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
interface f0/3
switchport mode trunk
switchport trunk allowed vlan 10,20
no shutdown
end
write memory
```

## Key Concepts
- VLAN = Layer 2 segmentation (security + broadcast control)
- Trunk = multiple VLANs over one link (802.1Q tagging)

## Verification Commands
```bash
show vlan brief
show interfaces trunk
```

## Troubleshooting Commands
```bash
show interfaces status
show running-config
```

## When to Use
- Different departments (Sales, HR, Production) need separation
- Limited switch ports but multiple VLANs required
- Inter-switch connectivity needed for VLAN communication
