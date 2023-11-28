# Cisco Cheat Sheet v.01
---
## Table of Contents
- **[Grundconfig](#grundconfig)**
- **[Shows](#shows)**
- **[Router Config](#router-config)**
- **[Switch Config](#switch-config)**
- **[Same Config](#same-config)**
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
#show access-list
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
#### NAT Outside Interface bei RIP und OSBF
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
### RIP Routing
#### RIP enable
```
(config)#router rip
(config-router)#version 2
(config-router)#no auto-summary
```
#### NW zu RIP hinzufügen
```
(config)#router rip
(config-router)#network 10.45.10.0 … NW Adresse
```
#### Default Routen weitergeben
---
```
(config)#router rip
(config-router)#default-information originate 
```
---
### OSBF Routing
#### OSBF enable
```
(config)#router ospf 1 oder (config)#router ospfv3
(config-router)#no auto-summary
```
#### Default Routen weitergeben
---
```
(config)#router osbf 1
(config-router)#default-information originate 
```
#### NW zu OSBF hinzufügen
```
(config-router)#network NetzwerkIP Wildcardmask area [Zahl] z.B
(config-router)#network 192.168.10.0 0.0.0.255 area 0
```
---
### Access Listen - Standard
#### Access List erstellen
```
(config)#access-list {List-ID} remark {Kommentar}
(config)#access-list {List-ID} [permit | deny] {IP} {Wildcard}
```
#### Access List Einträge hinzufügen
```
(config)#ip access-list standard {ACL-Name}
(config-std-nacl)#{Eintrag ID} [permit | deny] {IP-Adresse} {Wildcard}
```
#### Access Lists Matches clearen
```
#clear access-list counter {ACL-Name}
```
#### Access Lists Interface zuweisen
```
(config-if)#ip access-group {access-list-numer | access-list-name} {in | out}3
```
---
### VLAN
#### Subinterfaces
```
(config)#interface gigabitEthernet 0/1.50
(config-subif)#encapsulation dot1Q 50 
(config-subif)#ip address [IP] [Subnet]
```
---

## Switch-Config
---
### VLAN
#### VLAN erstellen
```
(config)#vlan [VLAN-ID]
(config-vlan)#name [VLAN-Name]
```
#### Ein VLAN löschen
```
(config)#no vlan [VLAN-ID]
```
#### Alles VLANs löschen
```
(config)#delete flash:vlan.dat
```
#### VLAN Interface(Access) zusweisen
```
(config)#interface [InterfaceID]
(config-if)#switchport mode access
(config-if)#switchport access vlan [VLAN-ID]
```
#### VLAN Interface(Trunk) zuweisen
```
(config)#interface [InterfaceID]
(config-if)#switchport mode trunk
(config-if)#switchport trunk encapsulation dot1q
(config-if)#switchport trunk native vlan [VLAN-ID]
(config-if)#switchport trunk allowed vlan [VLAN-List] //Switchporttrunk allowed vlan 10,20,30,99
```
---
### STP Spanning-Tree
#### Interface Spanning-Tree
```
(config-if)#spanning-tree portfast mode
```
#### Spanning-Tree aktivieren
```
(config)#spanning-tree vlan vlan-id
```
#### Spanning-Tree deaktivieren
```
(config)#no spanning-tree vlan vlan-id
```
#### Root Guard
```
(config)#interface fastEthernet 0/1
(config-if)#spanning-tree rootguard
```
#### BPDU Guard
```
(config-if)#spanning-tree portfast
(config)#spanning-tree portfast bpduguard
```
#### BPDU Filtering 1 Port
```
(config-if)#spanning-tree bpdufilter enable
```
#### BPDU Filtering all Ports
```
(config)#spanning-tree portfast bpdufilter default
```
---
### Same Config
#### SNMP Read Only
```
(config)#snmp-server community public RO
```
#### SNMP Write
```
(config)#snmp-server community private RW 
```