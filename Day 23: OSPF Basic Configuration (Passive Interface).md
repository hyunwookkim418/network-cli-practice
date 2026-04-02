# Day 23: OSPF Basic Configuration (Passive Interface)

Date: 2026-04-01

## Environment
- Cisco Packet Tracer
- Cisco Router

## Network Topology
```bash
PC LAN (192.168.60.0/24)
        |
     Router
     g0/0: 192.168.60.1
```

## CLI Commands
```bash
enable
configure terminal
interface g0/0
description LAN_Interface
ip address 192.168.60.1 255.255.255.0
no shutdown
exit
router ospf 1
router-id 1.1.1.1
network 192.168.60.0 0.0.0.255 area 0
passive-interface g0/0
end
write memory
```

## Key Concepts
- OSPF (Open Shortest Path First) is a link-state routing protocol used to dynamically exchange routing information between routers
- Router ID uniquely identifies each router in the OSPF domain and is critical for neighbor relationships
- Network Statement enables OSPF on matching interfaces and determines which networks are advertised
- Passive Interface prevents OSPF neighbor formation while still advertising the network → improves security and reduces unnecessary traffic

## When to Use
- When implementing dynamic routing between routers
- When you want to advertise LAN networks without forming neighbors
- In environments where LAN interfaces should not participate in routing adjacency
- Best practice in enterprise and data center networks

## Verification Commands
```bash
show ip ospf neighbor
show ip route ospf
show ip protocols
```

## Troubleshooting Commands
```bash
debug ip ospf adj
show ip ospf interface
show running-config | section ospf
```
