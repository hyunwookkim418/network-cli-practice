# Day 35: VTY Access Control (ACL + SSH)

Date: 2026-04-12

- 30-Second Summary: This configuration restricts remote access (VTY) using a standard ACL. Only devices in the 192.168.10.0/24 network are allowed to SSH into the device, while all other IPs are denied. This is a basic but powerful security control for network devices.

## CLI Configuration
```bash
enable
configure terminal
access-list 10 permit 192.168.10.0 0.0.0.255
access-list 10 deny any
line vty 0 4
access-class 10 in
password cisco
login
transport input ssh
end
write memory
```

## Key Concepts
- `access-list 10` → Defines permitted source IP range
- `access-class 10 in` → Applies ACL to VTY lines (remote access)
- `line vty 0 4` → Allows up to 5 simultaneous remote sessions
- `transport input ssh` → Restricts access to SSH only (secure)

## Verification Commands
```bash
show access-lists
show running-config | section vty
```

## When to Use
- Restrict remote admin access to trusted IP ranges
- Secure network devices in production environments
- Prevent unauthorized SSH/Telnet attempts
---
