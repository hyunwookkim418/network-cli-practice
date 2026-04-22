# Day 44: OSPF Basic Configuration

## Date
- 2026-04-21

## 30-Second Summary: OSPF allows routers to automatically share routes. By enabling OSPF on specific networks, routers form neighbor relationships and exchange routing information without manual static routes.
--- 

## Environment
- Cisco Router (Packet Tracer / Real Device)

## CLI Configuration

```bash
enable
configure terminal
interface g0/0
ip address 10.0.0.1 255.255.255.0
no shutdown
exit
router ospf 1
router-id 1.1.1.1
network 10.0.0.0 0.0.0.255 area 0
exit
interface g0/1
ip address 192.168.1.1 255.255.255.0
no shutdown
exit
router ospf 1
network 192.168.1.0 0.0.0.255 area 0
end
write memory
```

## Key Concepts
- OSPF dynamically exchanges routing information between routers
- `network` command enables OSPF on matching interfaces and advertises networks

## Verification Commands
```bash
show ip ospf neighbor
show ip route ospf
```

## Troubleshooting Tips
- Check interface status: `show ip interface brief`
- Verify OSPF enabled interfaces: `show ip ospf interface`
- Ensure same Area and subnet match for neighbor formation

---
