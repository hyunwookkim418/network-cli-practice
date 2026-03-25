# Day 15: NAT Overload (PAT) with Interface IP

Date: 2026-03-24

## Environment
- Cisco Packet Tracer
- Cisco Router (1941)

## Network Topology
```bash
PC LAN (192.168.10.0/24)
        |
   Router
   g0/0 (192.168.10.1)  → Inside
   g0/1 (203.0.113.10)  → Outside (Internet)
```

## CLI Commands
```bash
enable
configure terminal
interface g0/0
ip address 192.168.10.1 255.255.255.0
ip nat inside
no shutdown
exit
interface g0/1
ip address 203.0.113.10 255.255.255.0
ip nat outside
no shutdown
exit
access-list 1 permit 192.168.10.0 0.0.0.255
ip nat inside source list 1 interface g0/1 overload
end
write memory
```

## Key Concepts
- NAT Overload (PAT) = multiple internal IPs share one public IP
- ip nat inside / outside defines NAT direction
- ACL defines which internal IPs will be translated
- overload uses port numbers to allow many hosts to share one IP

## Verification Commands
```bash
show ip nat translations
show ip nat statistics
show access-lists
show ip interface brief
```

## Troubleshooting Commands
```bash
show running-config
debug ip nat
clear ip nat translation
```
