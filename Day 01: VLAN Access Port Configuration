# Day 01 – VLAN Access Port Configuration

Date: 2026-03-10  
Practice: 5 repetitions in Packet Tracer

## CLI Commands

```bash
enable
configure terminal
vlan 10
name SALES
exit
interface g0/1
switchport mode access
switchport access vlan 10
description PC_SALES
spanning-tree portfast
no shutdown
end
write memory
```

## What I Learned

- VLAN creates logical network segmentation.
- Access ports belong to a single VLAN.
- PortFast allows faster transition to forwarding state for end devices.

## Verification Commands

```bash
show vlan brief
show running-config
show interfaces status
```
