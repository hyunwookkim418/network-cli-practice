# Day 38: NAT Overload (PAT)

Date: 2026-04-15  

## Environment
- Cisco Packet Tracer  
- Router (e.g., 1941)

## CLI Configuration
```bash
enable
configure terminal
interface g0/0
ip nat inside
exit
interface g0/1
ip nat outside
exit
access-list 1 permit 192.168.50.0 0.0.0.255
ip nat inside source list 1 interface g0/1 overload
end
write memory
```

## Key Concepts
- NAT Overload (PAT) allows multiple internal devices to share one public IP using port numbers  
- Inside/Outside interface designation is required for NAT to function  

## Verification
```bash
show ip nat translations
show ip nat statistics
```

## Troubleshooting
```bash
show access-lists
show ip interface brief
```
