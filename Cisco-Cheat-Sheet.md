# Cisco Cheat Sheet v.01
---
## Table of Contents
- **[Grundconfig](#)**
- **[Shows](#)**
- **[Router Config](#)**
- **[Switch Config](#)**
---
### Grundconfig
#### Hostname  
```
(config)#hostname [Neuer Hostname]
```
#### Passwort
```
(config)#enable secret [Neues Passwort]
```
#### Konsolen Passwort
```
(config)#line console 0
(config-line)#password cisco
(config-line)#login
```
#### SSH Passwort
```
(config)#line vty 0 4 (Range kann auch 0 16 sein)
(config-line)#password [Neues Passwort]
(config-line)#login 
```
#### Passwörter Encrypten
```
(config)#service password-encryption
```
#### Interface - Static Config
```
(config)#interface [Interface] [Interface Nummer]
(config-if)#ip address [IP-Adress] [Subnet mask]
(config-if)#no Shutdown
```
#### Interface - DHCP Config
```
(config)#interface [Interface] [Interface Nummer]
(config-if)#ip address dhcp
(config-if)#no Shutdown
```
---
### Shows
#### CPU Auslastung
```
#show CPU
```
#### Routen anzeigen
```
#show ip route
```
#### VLAN Info
```
#show int [INT-ID] switchport
```
#### NAT Info
```
#show ip nat translations
```
#### ACL Info
```
#show access-lists
```
#### Mac Address Table
```
#show mac address-table [Weitere Optionen]
    Count … Zeigt anzahl der Einträge AN
    VLAN … Zeigt die MACS von einen VLAN an
#show access-lists … Zeigt die ACLs an
```
---
## Router-Config
---
### NAT Config
#### NAT Inside Interface
```
config#interfacce [Inside Interface]
(config-if)#ip nat inside
(config-if)#no shutdown
```
#### NAT Outside Interface
```
config#interfacce [Outside Interface]
(config-if)#ip nat outside
(config-if)#no shutdown
```
#### NAT Outside Interface bei RIP
```
config#interfacce [Outside Interface]
(config-if)#ip nat outside
(config-if)#no shutdown
(config-if)#passive interface
```
#### NAT Access-List
```
(config)#access-list 1 permit [NW Ip Adresse des erlaubten Netzwerkes] [Wildcard Adresse]
```
#### NAT enable 
```
(config)#ip nat inside source [Access Liste] [AL Nummer] interface [Externes Interface] [Int Nummer] overload
```
#### Portforwarding Static
```
(config)#ip nat inside source static <tcp/udp> <IP Server> <Port> <IP Außeninterface Router>
```
#### Portforwarding Dynamic
```
(config)#ip nat inside source static <tcp/udp> <IP Server> <Port> interface <Außeninterface Router>
```
---
### DHCP
#### DHCP Pool
```
(config)#ip dhcp excluded-address [Excluded address begin] [Exclude address end]
```
#### DHCP-Server
```
(config)#ip dhcp pool [Pool Name]
(dhcp-config)#network [NW Adresse] [SN Maske]
(dhcp-config)#default-router [Standart Gateway]
(dhcp-config)#dns-server [DNS Server IP]
```
---
### Statisches Routing
#### Static Route
```
(config)#ip route [ZielNW] [ZielNW Subnetmask] [Next Hop]
```
#### Default Route
```
(config)#ip route 0.0.0.0 0.0.0.0 [Next Hop]
```
---
### Rip Routing
#### Rip enable
```
(config)#router rip
(config-router)#version 2
(config-router)#no auto-summary
```
#### Default Routen weitergeben
---


<!-- ## Switch-Config
---
### VLAN -->

