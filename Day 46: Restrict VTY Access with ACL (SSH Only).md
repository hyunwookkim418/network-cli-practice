# Day 46: Restrict VTY Access with ACL (SSH Only)
Date: April 23, 2026

30-Second Summary: This configuration restricts remote access to network devices using a standard ACL applied to VTY lines. Only trusted IP ranges are allowed, and SSH is enforced for secure management, reducing the risk of unauthorized access and plaintext credential exposure.
---

## Environment
- Cisco Router / Switch (Packet Tracer or Real Device)

## CLI Configuration
```
enable
configure terminal
ip access-list standard MGMT_ONLY
permit 192.168.10.0 0.0.0.255
exit
line vty 0 4
access-class MGMT_ONLY in
password cisco
login
transport input ssh
end
write memory
```

## Key Concepts
- VTY Access Control: Only devices in 192.168.10.0/24 can remotely access the device
- Security Best Practice: Restrict remote access + allow only SSH (disable Telnet)

## Verification Commands
```
show access-lists
show running-config | section vty
```

## Troubleshooting Commands
```
debug ip ssh
show ip ssh
```
