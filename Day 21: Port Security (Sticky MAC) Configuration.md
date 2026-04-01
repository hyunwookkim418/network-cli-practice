# Day 21: Port Security (Sticky MAC) Configuration

Date: 2026-03-30

## Environment
- Cisco Packet Tracer
- Cisco Switch (2960)

## Network Topology
```bash
PC
 |
 | (Access VLAN 20)
 |
Switch (g0/1)
```

## CLI Commands
```bash
enable
configure terminal
interface g0/1
description User_Access_Port
switchport mode access
switchport access vlan 20
switchport port-security
switchport port-security maximum 2
switchport port-security violation restrict
switchport port-security mac-address sticky
no shutdown
end
write memory
```

## Key Concepts
- Port Security = Allows only specific MAC addresses on a switch port
- Sticky MAC = Automatically learns MAC addresses and saves them into the running configuration

## When to Use
- When you want to restrict a port to known devices only
- To prevent unauthorized devices (laptops, hubs, etc.) from connecting
- To secure sensitive VLANs (e.g., Finance, Production networks)

## Verification Commands
```bash
show port-security interface g0/1
show port-security address
show running-config
```

## Troubleshooting Commands
```bash
show port-security
show interface status
show mac address-table interface g0/1
```
