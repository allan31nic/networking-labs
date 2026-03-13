# Office Network VLAN Segmentation Lab
## Overview
This project demonstrates the design and implementation of segmented office network using VLANs in Cisco Packet Tracer.
The network separates deparments into different VLANs and subnets while implementing basic netwok security and dynamic IP assignment.

## Network Topology
![Network Topology](topology.pdf)

## Network Design
The network is divided into three departments:

| Department |   VLAN  |      Subnet     |
|------------|---------|-----------------| 
|     HR     | VLAN 10 | 192.168.10.0/29 |
|     IT     | VLAN 20 | 192.168.20.0/29 |
| Accounting | VLAN 30 | 192.168.30.0/29 |

### Security VLAN
|   VLAN  |          Purpose           |
|---------|----------------------------|
|VLAN 999 | Unused ports / Native VLAN |


All unused ports are assigned to VLAN 999 and administratively shut down.

## Router Configuration
Inter-VLAN routing is implemented using **Router-on-a-Stick**.

| Interface |   VLAN  |   Gateway    |
|-----------|---------|--------------|
| G0/0/1.10 | VLAN 10 | 192.168.10.1 |
| G0/0/1.20 | VLAN 20 | 192.168.20.1 |
| G0/0/1.30 | VLAN 30 | 192.168.30.1 |


## DHCP Configuration
The router provides DHCP services for each VLAN.

Example:
ip dhcp pool HR
network 192.168.10.0 255.255.255.248
default-router 192.168.10.1

## IPv6 Configuration

The network also supports IPv6 using:
- SLAAC (Stateless Address Autoconfiguration)
- DHCPv6 for additional configuration

Example IPv6 prefixes:

|    VLAN    |    IPv6 Prefix   |
|------------|------------------|
|     HR     | 2001:db8:10::/64 |
|     IT     | 2001:db8:20::/64 |
| Accounting | 2001:db8:30::/64 |


## Network Security

The following security mechanisms were implemented:

- Port security (Sticky MAC)
- Maximum MAC addresses per port
- Unused ports assigned to VLAN 999
- Native VLAN changed from default
- SSH enabled for remote management
- Telnet disabled
- Console and VTY password protection
- Password encryption enabled

## Technologies Used

- Cisco Packet Tracer
- VLAN Segmentation
- Router-on-a-Stick
- DHCP
- IPv6 SLAAC
- DHCPv6
- SSH Remote Management

## Project Files
packet-tracer/

## Author

Allan Collado
Networking & Software Development Student
