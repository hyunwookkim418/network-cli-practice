# Day 02: VLAN Access Port Configuration (Review)

Date: 2026-03-11  

## Environment

- Cisco Packet Tracer  
- Cisco Switches and Routers

## CLI Commands

```bash
enable
configure terminal
vlan 20
name ENGINEERING
exit
interface g0/2
switchport mode access
switchport access vlan 20
description PC_ENGINEERING
spanning-tree portfast
no shutdown
end
write memory
```

## Key Concept

- An access port belongs to a single VLAN and connects end devices such as PCs or printers.  
- The message `%SYS-5-CONFIG_I: Configured from console by console` indicates that the device configuration was modified from the console.

## Verification Commands

```bash
show vlan brief
show running-config
show interfaces status
```

## Troubleshooting Commands

```bash
show interfaces g0/2 switchport
show spanning-tree interface g0/2
```
