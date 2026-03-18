# Day 07 – OSPF Basic Configuration (Single Area)

Date: 2026-03-16  

## Environment

- Cisco Packet Tracer  
- Cisco Routers (1941)

## Network Topology
LAN_A (192.168.10.0/24)
|
| 192.168.10.1
RouterA
|
| 10.1.1.1/30
|
RouterB
|
| 10.1.1.2/30
|
LAN_B (192.168.20.0/24)


---

# RouterA Configuration

## CLI Commands

```bash
enable
configure terminal

interface g0/0
description LAN_A
ip address 192.168.10.1 255.255.255.0
no shutdown
exit

interface g0/1
description Link_to_RouterB
ip address 10.1.1.1 255.255.255.252
no shutdown
exit

router ospf 1
network 192.168.10.0 0.0.0.255 area 0
network 10.1.1.0 0.0.0.3 area 0

end
write memory

# RouterB Configuration

## CLI Commands

enable
configure terminal

interface g0/1
description Link_to_RouterA
ip address 10.1.1.2 255.255.255.252
no shutdown
exit

interface g0/0
description LAN_B
ip address 192.168.20.1 255.255.255.0
no shutdown
exit

router ospf 1
network 10.1.1.0 0.0.0.3 area 0
network 192.168.20.0 0.0.0.255 area 0

end
write memory

## Key Concept

- OSPF dynamically advertises connected networks and builds routing tables using SPF (Shortest Path First).
- Neighbor adjacency is formed only when routers share the same subnet, area, and OSPF parameters.

## Verification Commands
show ip ospf neighbor
show ip route
show ip ospf interface

## Troubleshooting Commands
show ip interface brief
show ip ospf
show ip ospf database
