# Day 27: EtherChannel (LACP) Configuration & Verification

Date: 2026-04-04

## Environment
- Cisco Packet Tracer
- Cisco Switch (2960)

## CLI Commands
```bash
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

## Verification Commands
```bash
show etherchannel summary
show interfaces port-channel 1
show interfaces trunk
show lacp neighbor
```

## Expected Output (Healthy State)
```bash
Group  Port-channel  Protocol  Ports
1      Po1(SU)       LACP      Gi0/1(P) Gi0/2(P)
```

## Key Concepts
- EtherChannel = Multiple physical links → One logical link
- LACP (active mode) = Dynamic negotiation
- Port-channel interface = Real traffic path
- Both sides MUST match configuration

## Common Issues
```bash
| Symptom | Meaning |
|--------|--------|
| (I) | Individual (not bundled) |
| (D) | Down |
| suspended | Config mismatch |
| No Po1 | EtherChannel not formed |
| No LACP neighbor | Other side misconfigured |
```

## When to Use
- Switch uplink design
- Redundancy (high availability)
- Bandwidth aggregation
