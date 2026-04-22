# Day 43: VLAN & Trunk Configuration

## Date
2026-04-21

## 30-Second Summary: VLANs separate network segments logically, while trunk links allow multiple VLANs to pass between switches. Proper configuration ensures communication across departments like SALES and HR while maintaining segmentation.
--- 

## Environment
- Cisco Switch (Packet Tracer / Real Device)

## CLI Configuration
```
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
interface g0/3
switchport mode trunk
switchport trunk allowed vlan 10,20
no shutdown
end
write memory
```

## Key Concepts
- VLANs segment Layer 2 networks to improve security and reduce broadcast traffic
- Trunk ports carry multiple VLANs using 802.1Q tagging between switches

## Verification Commands

```
show vlan brief
show interfaces trunk
```

## Troubleshooting Tips
- Check VLAN existence: `show vlan brief`
- Verify trunk allowed VLANs mismatch
- Ensure access ports are assigned to correct VLAN

---

