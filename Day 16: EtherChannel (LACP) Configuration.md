# Day 16: EtherChannel (LACP) Configuration

Date: 2026-03-25

## Environment
- Cisco Packet Tracer
- Cisco Switch (2960)

## Network Topology
```bash
Switch A (g0/1, g0/2)
        ||
        ||  EtherChannel (Po1)
        ||
Switch B (g0/1, g0/2)
```

## CLI Commands
```bash enable
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
- EtherChannel = Bundles multiple physical links into one logical link
- Uses LACP → negotiation starts with `mode active`
- The Port-channel interface is the actual traffic-handling interface
- Trunk configuration must be applied on the Port-channel interface

## Verification Commands
```bash show etherchannel summary
show interfaces port-channel 1
show interfaces trunk
```
