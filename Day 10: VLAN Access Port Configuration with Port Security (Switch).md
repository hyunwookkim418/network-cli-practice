# Day 10: VLAN Access Port Configuration with Port Security (Switch)

Date: 2026-03-19

## Environment
- Cisco Packet Tracer
- Cisco Switch (2960)

## Network Topology
bash```
PC
|
| (Access VLAN 10)
|
Switch (g0/1)
```

# Switch Configuration
## CLI Commands
bash```
enable
configure terminal

vlan 10
name SALES

interface g0/1
switchport mode access
switchport access vlan 10
spanning-tree portfast
spanning-tree bpduguard enable
no shutdown
exit

end
write memory
```

## Key Concept
- VLAN 10 is created and assigned to the SALES department
- Access port (g0/1) is configured for end device (PC)
- PortFast enables immediate forwarding state (no STP delay)
- BPDU Guard disables the port if a switch is mistakenly connected (basic security)

## Verification Commands
bash```
show vlan brief
show running-config
show spanning-tree interface g0/1
```

## Troubleshooting Commands
bash```
show interface status
show mac address-table
show spanning-tree
```
