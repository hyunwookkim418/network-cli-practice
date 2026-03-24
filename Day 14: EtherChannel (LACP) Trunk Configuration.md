# Day 14: EtherChannel (LACP) Trunk Configuration

Date: 2026-03-23

## Environment
- Cisco Packet Tracer
- Cisco Switch (2960)

## Network Topology
```bash
SwitchA (g0/1, g0/2)
    ||
    ||  EtherChannel (Po1)
    ||
SwitchB (g0/1, g0/2)
```

# Switch Configuration
## CLI Commands
```bash
enable
configure terminal
interface range g0/1 - 2
switchport mode trunk
channel-group 1 mode active
exit
interface port-channel 1
switchport mode trunk
description Uplink_to_Core
no shutdown
end
write memory
```

## Key Concepts
- EtherChannel bundles multiple physical links into a single logical link
- LACP (802.3ad) is used → mode active initiates negotiation
- Trunk configuration must be applied on both physical interfaces and the Port-Channel
- The Port-Channel interface is the actual interface that forwards traffic

## Verification Commands
```bash
show etherchannel summary
show interfaces trunk
show running-config interface port-channel 1
```

## Troubleshooting Commands
```bash
show etherchannel port-channel
show lacp neighbor
show interfaces status
```
