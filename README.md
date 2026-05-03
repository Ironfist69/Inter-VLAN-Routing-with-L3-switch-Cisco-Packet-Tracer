# Inter-VLAN-Routing-with-L3-switch-Cisco-Packet-Tracer-
## Overview
This project demonstrates the implementation of Inter-VLAN Routing using a combination of Layer 2 and Layer 3 switches in Cisco Packet Tracer. The network is segmented into multiple VLANs to improve scalability, and management.

## Objectives
- Configure multiple VLANs across switches
- Enable communication between VLANs using L3 switch routing
- Implement trunking between switches
- Test connectivity across VLANs

## Topology
<img width="1428" height="598" alt="2053" src="https://github.com/user-attachments/assets/7d15d0b3-9ecb-435f-b4fb-49dc8297afbc" />


- VLAN 10 → PCs (User network)
- VLAN 20 → Servers (and some PCs)
- VLAN 30 → Wi-Fi / Laptop network (and some PCs)
- VLAN 50 → Printer network
- VLAN 100 → Native VLAN for uplink

## Configuration
### L3 Switch
- Enabling IP Routing
> ip routing
- VLAN creation (For VLAN 10, same procedure for 20,30,50)
>Switch(config)# vlan 10
>
>Switch(config-vlan)# name [vlan10]
>
>Switch(config-vlan)# exit
>
>Switch(config)# int vlan 10
>
>Switch(config-if)# ip address 192.168.10.1 255.255.255.0
>
>Switch(config-if)# no sh
>
- Uplink Configuration with L2 switch g1/0/1 [same for g1/0/2/, g1/0/3]
> Switch(config)# int range g1/0/1-3
>
> Switch(config-if)# switchport mode trunk (There are three modes dynamic, access, trunk)
> 
> Switch(config-if)# switchport trunk allowed vlan 10, vlan 20, vlan 30, vlan 50
>
> Switch(config-if)# switchport trunk native vlan 100
>
By default encapsulation IEEE 802.1q (Open-Source Standard)
