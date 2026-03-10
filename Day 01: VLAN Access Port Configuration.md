# Day 01 – VLAN Access Port Configuration

Date: 2026-03-10  
## Environment

- Cisco Packet Tracer  
- Cisco 2960 Switch

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

## Key Concept

- An access port belongs to a single VLAN and connects end devices such as PCs or printers.  
- A VLAN logically separates networks within a Layer 2 switch, allowing devices in different VLANs to be isolated even if they share the same physical switch.

## Verification Commands

```bash
show vlan brief
show running-config
show interfaces status
```

## Troubleshooting Commands

```bash
show interfaces g0/1 switchport
show spanning-tree interface g0/1
```
