# Day 06: Edge Router to Upstream Router Default Route

Date: 2026-03-15  

## Environment

- Cisco Packet Tracer  
- Cisco Routers

## Network Topology

```
PC LAN (192.168.1.0/24)
        |
        | 192.168.1.1
     Edge Router (RouterA)
        |
        | 10.1.1.1/30
        |
     Upstream Router (RouterB)
        |
        | 10.1.1.2/30
        |
        ISP / Internet
```

---

# RouterA Configuration (Edge Router)

## CLI Commands

```bash
enable
configure terminal

interface g0/0
description Link_to_RouterB
ip address 10.1.1.1 255.255.255.252
no shutdown
exit

interface g0/1
description LAN_Interface
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

ip route 0.0.0.0 0.0.0.0 10.1.1.2

end
write memory
```

---

# RouterB Configuration (Upstream Router)

## CLI Commands

```bash
enable
configure terminal

interface g0/0
description Link_to_RouterA
ip address 10.1.1.2 255.255.255.252
no shutdown

end
write memory
```

---

## Key Concept

- An **edge router** connects an internal LAN to an external network or upstream router.  
- A **default route (0.0.0.0/0)** forwards unknown traffic toward the upstream router.

---

## Verification Commands

```bash
show ip route
show ip interface brief
show running-config
```

---

## Troubleshooting Commands

```bash
show ip route static
show interfaces g0/0
show running-config interface g0/0
```
