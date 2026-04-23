# Day 45: EtherChannel (LACP) + Trunk Configuration for Bandwidth and Redundancy

Date: 2026-04-22
30-Second Summary: EtherChannel allows multiple physical interfaces to be bundled into a single logical link, increasing bandwidth and providing redundancy. By configuring the Port-Channel as a trunk, multiple VLANs can traverse the same link efficiently. This design improves network performance, prevents STP from blocking redundant links, and ensures high availability.  

## Environment
- Cisco Packet Tracer
- Switch (Layer 2)

## CLI Configuration
```
enable
configure terminal
interface range g0/1 - 2
channel-group 1 mode active
exit
interface port-channel 1
switchport mode trunk
switchport trunk allowed vlan 10,20,30
no shutdown
end
write memory
```

## Key Concepts
- EtherChannel (LACP): Combines multiple physical interfaces into one logical link to increase bandwidth and provide redundancy.
- Trunk Port Configuration: Allows multiple VLANs (10, 20, 30) to pass through a single link using 802.1Q tagging.

## Verification Commands
```
show etherchannel summary
show interfaces port-channel 1
show interfaces trunk
```

## Troubleshooting Tips
```
show running-config interface g0/1
show running-config interface port-channel 1
show spanning-tree
```
- Ensure both interfaces have identical configurations (speed, duplex, VLAN settings).
- If EtherChannel fails, check LACP mode (active/active or active/passive).
- Verify VLANs are allowed on the trunk.
