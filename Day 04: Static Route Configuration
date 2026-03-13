# Day 04: Static Route Configuration

Date: 2026-03-13  

## Environment

- Cisco Packet Tracer  
- Cisco Switches and Routers

## CLI Commands

```bash
enable
configure terminal
interface g0/0
description Link_to_RouterB
ip address 192.168.10.1 255.255.255.0
no shutdown
exit
ip route 192.168.20.0 255.255.255.0 192.168.10.2
ip route 192.168.30.0 255.255.255.0 192.168.10.2
end
write memory
```

## Key Concept

- A static route manually tells the router which next-hop IP address to use in order to reach a remote network.  
- In `ip route 192.168.20.0 255.255.255.0 192.168.10.2`, the destination network is `192.168.20.0/24` and the next hop is `192.168.10.2`, which is Router B’s interface IP on the directly connected network.

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
