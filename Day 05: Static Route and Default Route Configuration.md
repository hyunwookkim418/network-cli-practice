# Day 05: Static Route and Default Route Configuration

Date: 2026-03-14  

## Environment

- Cisco Packet Tracer  
- Cisco Switches and Routers

## Network Topology

```
PC LAN (192.168.10.0/24)
        |
   RouterA
   g0/0: 192.168.10.1
        |
        | 192.168.10.0/24
        |
   RouterB (default route)
   g0/0: 192.168.10.2
        |
       / \
      /   \___________
192.168.50.0/24      ISP
 Server LAN          203.0.113.1
```

# RouterA Configuration

## CLI Commands

```bash
enable
configure terminal
interface g0/0
description Link_to_RouterB
ip address 192.168.10.1 255.255.255.0
no shutdown
exit
ip route 192.168.50.0 255.255.255.0 192.168.10.2
ip route 0.0.0.0 0.0.0.0 192.168.10.2
end
write memory
```

---

# RouterB Configuration

## CLI Commands

```bash
enable
configure terminal
interface g0/0
description Link_to_RouterA
ip address 192.168.10.2 255.255.255.0
no shutdown
exit
ip route 0.0.0.0 0.0.0.0 203.0.113.1
end
write memory
```

---

## Key Concept

- A **static route** manually defines the next-hop IP address to reach a remote network.  
- A **default route (0.0.0.0/0)** is used when no more specific route exists in the routing table and typically forwards traffic toward an ISP.

## Verification Commands

```bash
show ip route
show ip interface brief
show running-config
```

## Troubleshooting Commands

```bash
show ip route static
show interfaces g0/0
show running-config interface g0/0
```
