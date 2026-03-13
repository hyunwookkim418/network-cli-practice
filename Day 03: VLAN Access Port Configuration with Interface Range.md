# Day 03: VLAN Access Port Configuration with Interface Range

Date: 2026-03-12  

## Environment

- Cisco Packet Tracer  
- Cisco Switches and Routers

## CLI Commands

```bash
enable
configure terminal
vlan 30
name HR
exit
interface range fa0/1 - 10
switchport mode access
switchport access vlan 30
description HR_PC
spanning-tree portfast
no shutdown
end
write memory
```

## Key Concept

- The `interface range` command allows multiple interfaces to be configured simultaneously, which significantly speeds up switch configuration.  
- Access ports are typically used to connect end devices and belong to a single VLAN, allowing traffic segmentation within a Layer 2 switch.

## Verification Commands

```bash
show vlan brief
show running-config
show interfaces status
```

## Troubleshooting Commands

```bash
show interfaces fa0/1 switchport
show spanning-tree interface fa0/1
```
