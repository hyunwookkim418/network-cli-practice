# Day 31: Static Route + Basic Interface Configuration

Date: 2026-04-08

30-Second Summary: Configured LAN and WAN interfaces, then applied a default static route to enable external network communication. `ip route 0.0.0.0 0.0.0.0 203.0.113.1` creates a default route that matches all unknown destinations. It tells the router to forward any traffic it doesn’t recognize to the next-hop IP (usually the ISP gateway). This setup is commonly used in small networks where dynamic routing is unnecessary.

## Environment
- Cisco Packet Tracer
- Cisco Router

## CLI Commands
```bash
enable
configure terminal
interface g0/0
description LAN_Interface
ip address 192.168.20.1 255.255.255.0
no shutdown
exit
access-list 1 permit 192.168.20.0 0.0.0.255
ip route 0.0.0.0 0.0.0.0 203.0.113.1
interface g0/1
description WAN_Interface
ip address 203.0.113.2 255.255.255.0
no shutdown
end
write memory
```

## Key Concepts
- Static Route = Manually defines the path to reach external networks
- Default Route (0.0.0.0/0) = Sends all unknown traffic to the ISP

## When to Use
- Small networks with a single exit path
- When you want full control over routing behavior
- When dynamic routing (OSPF/EIGRP) is unnecessary

## Verification Commands
```bash
show ip interface brief
show ip route
ping 8.8.8.8
```

## Troubleshooting
```bash
show running-config
show ip route
debug ip routing
```
