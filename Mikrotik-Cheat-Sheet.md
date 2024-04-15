# Mikrotik Cheat Sheet v1.01
## Table of Contents
- **[Grundconfig](#grundconfig)** 
- **[Interface](#interface)**
- **[Shows](#shows)**
- **[DHCP](#dhcp)**
- **[Routing](#static-routing)**
- **[VLAN](#vlans)**
---
### Grundconfig
#### Change name
```console
/system identity set name=MTR-05-10
```
#### SSH Config
```mikrotik
/ip service set ssh address= <IP legt fest aus welchen Netzwerk man auf den Router zugreifen kann>
```
#### Tools
```mikrotik
/tool profile cpu=all
/tool profile
/system resource print
```
#### add DNS entry
```mikrotik
/ip dns static> add name=www.example.com address=<Adresse des Zielgeräts>
```
---
### Interface
#### add ip address
```mikrotik
/ip address add
```
#### Change interface name
```mikrotik
/interface ethernet
set [ find default-name=ether2 ] name=LAN
set [ find default-name=ether3 ] name=LAN2
set [ find default-name=ether4 ] name=LAN3
set [ find default-name=ether1 ] name=WAN
```
#### Interface comment
```mikrotik
/interface ethernet set [ find default-name=ether2 ] comment= Link
```
---
### Shows
#### Interface status
```mikrotik
/interface pr
/ip address print
/interface print detail
```
#### show all interfaces
```mikrotik
/interface export
```
#### show Mac Address Table
```mikrotik
/interface bridge host print count-only
/ip settings print
```
#### show VLANs
```mikrotik
/interface vlan> print 
```
#### show DHCP addresses
```mikrotik
/ip dhcp-server lease print
```
#### show route table
```mikrotik
/ip route print where routing-mark=main
```
---
### DHCP
#### DHCP Pool
```mikrotik
/ip pool add name=<Name des Pools> ranges=<Range des Pool (10.0.10.160-10.010.180)>
```
#### DHCP Server
```mikrotik
/ ip dhcp setup
		
Select interface to run DHCP server on 
dhcp server interface: bridgeLocal
		
Select network for DHCP addresses 
dhcp address space: 10.0.10.128/26
		
Select gateway for given network 
ateway for dhcp network: 10.0.10.129
		
If this is remote network, enter address of DHCP relay 
dhcp relay: 10.0.10.129
		
Select pool of ip addresses given out by DHCP server 
addresses to give out: 10.0.10.160-10.0.10.180
		
Select DNS servers 
dns servers: 8.8.8.8
```
---
### Static Routing
#### IP Route
```mikrotik
/ip route add dst-address= <Zielnetzwerk/Subnetzmaske> gateway= <Gateway IPv4>
/ip route add gateway=10.23.0.1 dst-address=10.23.0.0/24 
```
---
### RIP Dynamic Routing
#### rip instance
```mikrotik
/routing rip instance
add disabled=no name=rip-instance-1 redistribute=connected,rip
```
#### rip interface-template
```mikrotik
/routing rip interface-template
add disabled=no instance=rip-instance-1 interfaces=all
```
### add rip network
```mikrotik
/routing rip network network=<networkAddress>.<prefix>
```
#### add rip neighbor
```mikrotik
/routing rip neighbor address=<ipAddress>.<prefix>
```
#### rip keys
```mikrotik
/routing rip keys
```
#### routing rip interface
```mikrotik
/routing rip interface
```
---
### OSPF Routing
#### create OSPF instance
```mikrotik
/routing ospf instanceadd disabled=no name="OSPF" originate-default=always {gibt die default Route weiter}
```
#### define area
```mikrotik
/routing ospf area add disabled=no instance="OSPF " name="Area 0"
```
#### add network to OSPF
```mikrotik
/routing ospf interface-template add area="Area 0" disabled=no interfaces={interface where the nw is} networks={NW you wanna add}
```
---
### NAT
#### NAT/PAT
```mikrotik
/ip firewall nat add chain=srcnat src-address={alle NWs die ins Internet dürfen} action=masquerade out-interface=ether3

#wenn alle 
/ip firewall nat add chain=srcnat src-address=0.0.0.0/0 action=masquerade out-interface=ether3
```

#### portforwarding
```mikrotik
/ip firewall nat add action=dst-nat chain=dstnat dst-address=x.x.x.x dst-port=8090 protocol=tcp to-addresses=IP Server
```
---
### VLANS
#### interface vlan
```mikrotik
/interface vlan 
add name=vlan1 vlan-id=11 interface=ether1 
add name=vlan2 vlan-id=12 interface=vlan1 
```
#### add IP to VLAN
```mikrotik
add address=10.10.10.5/24 interface=VLAN2
```
---



