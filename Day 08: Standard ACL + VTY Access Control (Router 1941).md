Day 08: Standard ACL + VTY Access Control (Router 1941)

Date: 2026-03-17

Environment

Cisco Packet Tracer

Cisco Router (1941)

Network Topology
PC (192.168.10.0/24)
|
| 192.168.10.1
Router (g0/0)
|
| (Other Networks)
Router Configuration
CLI Commands
enable
configure terminal

access-list 10 permit 192.168.10.0 0.0.0.255
access-list 10 deny any

interface g0/0
ip access-group 10 in
exit

line vty 0 4
access-class 10 in
transport input ssh

end
write memory
Key Concept

Standard ACL filters traffic based on source IP only

ip access-group applies ACL to interface traffic (data plane)

access-class applies ACL to VTY access (control plane)

transport input ssh ensures secure remote access only

Verification Commands
show access-lists
show ip interface g0/0
show running-config
Troubleshooting Commands
show ip interface brief
debug ip packet
show line vty 0 4
