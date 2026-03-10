Day 01 – VLAN Access Port Configuration
Date: 2026-03-10

Environment
Cisco Packet Tracer
Cisco 2960 Switch

CLI Commands
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

Key Concept

Access Port
An access port carries traffic for only one VLAN and typically connects end devices such as PCs or printers.

VLAN Segmentation
A VLAN logically separates networks within a Layer 2 switch, allowing devices in different VLANs to be isolated even if they share the same physical switch.

Verification Commands
show vlan brief
show running-config
show interfaces status

Troubleshooting Commands
show interfaces g0/1 switchport
show spanning-tree interface g0/1
