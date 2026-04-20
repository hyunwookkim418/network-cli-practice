Day 42: Network CLI Practice

Date: 2026-04-19

30-Second Summary: A default static route directs all unknown traffic to a specified next-hop. In this lab, I configured a route to forward outbound traffic to an upstream router. This is essential for internet connectivity and simple network designs.

## Environment
- Cisco Router (Packet Tracer)

## CLI Commands
```bash
enable
configure terminal
interface g0/0
ip address 10.0.0.1 255.255.255.252
no shutdown
exit
interface g0/1
ip address 192.168.1.1 255.255.255.0
no shutdown
exit
ip route 0.0.0.0 0.0.0.0 10.0.0.2
end
write memory
```

## Key Concepts
- Static default route (0.0.0.0/0) sends all unknown traffic to next-hop
- Used for internet access or upstream routing

## Verification Commands
```bash
show ip route
show ip interface brief
```

## Troubleshooting Commands
```bash
show running-config
ping 10.0.0.2
traceroute 8.8.8.8
```
