# Cisco Cheat Sheet v1.02
---
## Table of Contents
- [Cisco Cheat Sheet v1.02](#cisco-cheat-sheet-v102)
  - [Table of Contents](#table-of-contents)
    - [Grundconfig](#grundconfig)
      - [Hostname](#hostname)
      - [Passwort](#passwort)
      - [Konsolen Passwort](#konsolen-passwort)
      - [SSH Passwort](#ssh-passwort)
      - [Passwörter Encrypten](#passwörter-encrypten)
      - [Interface - Static Config](#interface---static-config)
      - [Interface - DHCP Config](#interface---dhcp-config)
    - [Shows](#shows)
      - [CPU Auslastung](#cpu-auslastung)
      - [Routen anzeigen](#routen-anzeigen)
      - [VLAN Info](#vlan-info)
      - [NAT Info](#nat-info)
      - [ACL Info](#acl-info)
      - [Mac Address Table](#mac-address-table)
      - [Port-channel](#port-channel)
      - [Ether-channel summary](#ether-channel-summary)
      - [Etherchannel port-channel](#etherchannel-port-channel)
      - [show interface etherchannel](#show-interface-etherchannel)
      - [VTP](#vtp)
  - [Router-Config](#router-config)
    - [NAT Config](#nat-config)
      - [NAT Inside Interface](#nat-inside-interface)
      - [NAT Outside Interface](#nat-outside-interface)
      - [NAT Outside Interface bei RIP und OSBF](#nat-outside-interface-bei-rip-und-osbf)
      - [NAT Access-List](#nat-access-list)
      - [NAT enable](#nat-enable)
      - [Portforwarding Static](#portforwarding-static)
      - [Portforwarding Dynamic](#portforwarding-dynamic)
    - [DHCP](#dhcp)
      - [DHCP Pool](#dhcp-pool)
      - [DHCP-Server](#dhcp-server)
    - [Statisches Routing](#statisches-routing)
      - [Static Route](#static-route)
      - [Default Route](#default-route)
    - [RIP Routing](#rip-routing)
      - [RIP enable](#rip-enable)
      - [NW zu RIP hinzufügen](#nw-zu-rip-hinzufügen)
      - [Default Routen weitergeben](#default-routen-weitergeben)
      - [Default Routen weitergeben (IPv6 RIP)](#default-routen-weitergeben-ipv6-rip)
      - [Passive Interface](#passive-interface)
      - [Redistribute OSPF into RIP](#redistribute-ospf-into-rip)
    - [OSPF Routing](#ospf-routing)
      - [OSPF enable](#ospf-enable)
      - [OSPFv3](#ospfv3)
      - [Default Routen weitergeben](#default-routen-weitergeben-1)
      - [NW zu OSPF hinzufügen](#nw-zu-ospf-hinzufügen)
      - [Passiv Interface](#passiv-interface)
      - [Von Broadcast zu Point-zu-Point wechseln](#von-broadcast-zu-point-zu-point-wechseln)
      - [Redistribute RIP into OSPF](#redistribute-rip-into-ospf)
    - [Basic BGP Configuration](#basic-bgp-configuration)
      - [Local Pref/ Next Hop Self](#local-pref-next-hop-self)
      - [Metric](#metric)
      - [Weight](#weight)
      - [Equal Load Balancing](#equal-load-balancing)
      - [Unequal Load Balancing](#unequal-load-balancing)
      - [Default Route](#default-route-1)
      - [Test BGP](#test-bgp)
    - [Access Listen - Standard](#access-listen---standard)
      - [Access List erstellen](#access-list-erstellen)
      - [Access List Einträge hinzufügen](#access-list-einträge-hinzufügen)
      - [Access Lists Matches clearen](#access-lists-matches-clearen)
      - [Access Lists Interface zuweisen](#access-lists-interface-zuweisen)
    - [Access Listen - Extended](#access-listen---extended)
    - [Access List erstellen und Einträge hinzufügen](#access-list-erstellen-und-einträge-hinzufügen)
    - [Access List auf Interface zuweisen](#access-list-auf-interface-zuweisen)
    - [Acces List löschen](#acces-list-löschen)
    - [VLAN](#vlan)
      - [Subinterfaces](#subinterfaces)
    - [Etherchannel](#etherchannel)
      - [Portchannel](#portchannel)
    - [HSRP](#hsrp)
    - [VRRP](#vrrp)
  - [Switch-Config](#switch-config)
    - [VLAN](#vlan-1)
      - [VLAN erstellen](#vlan-erstellen)
      - [Ein VLAN löschen](#ein-vlan-löschen)
      - [Alles VLANs löschen](#alles-vlans-löschen)
      - [VLAN Interface(Access) zusweisen](#vlan-interfaceaccess-zusweisen)
      - [VLAN Interface(Trunk) zuweisen](#vlan-interfacetrunk-zuweisen)
    - [VLAN Layer 3 Switch Routing](#vlan-layer-3-switch-routing)
      - [VLAN Interfaces erstellen](#vlan-interfaces-erstellen)
      - [Routing einschalten](#routing-einschalten)
    - [STP Spanning-Tree](#stp-spanning-tree)
      - [Interface Spanning-Tree](#interface-spanning-tree)
      - [Spanning-Tree aktivieren](#spanning-tree-aktivieren)
      - [Spanning-Tree deaktivieren](#spanning-tree-deaktivieren)
      - [Root Guard](#root-guard)
      - [BPDU Guard](#bpdu-guard)
      - [BPDU Filtering 1 Port](#bpdu-filtering-1-port)
      - [BPDU Filtering all Ports](#bpdu-filtering-all-ports)
      - [Port-Security](#port-security)
    - [VTP](#vtp-1)
      - [VTP Modes](#vtp-modes)
    - [Router \& Switch Config](#router--switch-config)
      - [SNMP Read Only](#snmp-read-only)
      - [SNMP Write](#snmp-write)


### Grundconfig
#### Hostname  
```console
(config)#hostname [Neuer Hostname]
```
#### Passwort
```console
(config)#enable secret [Neues Passwort]
```
#### Konsolen Passwort
```console
(config)#line console 0
(config-line)#password cisco
(config-line)#login
```
#### SSH Passwort
```console
(config)#line vty 0 4 (Range kann auch 0 16 sein)
(config-line)#password [Neues Passwort]
(config-line)#login 
```
#### Passwörter Encrypten
```console
(config)#service password-encryption
```
#### Interface - Static Config
```console
(config)#interface [Interface] [Interface Nummer]
(config-if)#ip address [IP-Adress] [Subnet mask]
(config-if)#no Shutdown
```
#### Interface - DHCP Config
```console
(config)#interface [Interface] [Interface Nummer]
(config-if)#ip address dhcp
(config-if)#no Shutdown
```
---
### Shows
#### CPU Auslastung
```console
#show CPU
```
#### Routen anzeigen
```console
#show ip route
```
#### VLAN Info
```console
#show int [INT-ID] switchport
```
#### NAT Info
```console
#show ip nat translations
```
#### ACL Info
```console
#show access-list
```
#### Mac Address Table
```console
#show mac address-table [Weitere Optionen]
    Count … Zeigt anzahl der Einträge AN
    VLAN … Zeigt die MACS von einen VLAN an
#show access-lists … Zeigt die ACLs an
```
#### Port-channel
```console
#show interface port-channel
```
#### Ether-channel summary
```console
#show etherchannel summary
```
#### Etherchannel port-channel
```console
#show etherchannel port-channel
```
#### show interface etherchannel
```console
#show interface etherchannel
```
#### VTP
```console
#show vtp status
```
---
## Router-Config
---
### NAT Config
#### NAT Inside Interface
```console
config#interface [Inside Interface]
(config-if)#ip nat inside
(config-if)#no shutdown
```
#### NAT Outside Interface
```console
config#interface [Outside Interface]
(config-if)#ip nat outside
(config-if)#no shutdown
```
#### NAT Outside Interface bei RIP und OSBF
```console
config#interface [Outside Interface]
(config-if)#ip nat outside
(config-if)#no shutdown
(config-if)#passive interface
```
#### NAT Access-List
```console
(config)#access-list 1 permit [NW Ip Adresse des erlaubten Netzwerkes] [Wildcard Adresse]
```
#### NAT enable 
```console
(config)#ip nat inside source [Access Liste] [AL Nummer] interface [Externes Interface] [Int Nummer] overload
```
#### Portforwarding Static
```console
(config)#ip nat inside source static <tcp/udp> <IP Server> <Port> <IP Außeninterface Router>
```
#### Portforwarding Dynamic
```console
(config)#ip nat inside source static <tcp/udp> <IP Server> <Port> interface <Außeninterface Router>
```
---
### DHCP
#### DHCP Pool
```console
(config)#ip dhcp excluded-address [Excluded address begin] [Exclude address end]
```
#### DHCP-Server
```console
(config)#ip dhcp pool [Pool Name]
(dhcp-config)#network [NW Adresse] [SN Maske]
(dhcp-config)#default-router [Standart Gateway]
(dhcp-config)#dns-server [DNS Server IP]
```
---
### Statisches Routing
#### Static Route
```console
(config)#ip route [ZielNW] [ZielNW Subnetmask] [Next Hop]
```
#### Default Route
```console
(config)#ip route 0.0.0.0 0.0.0.0 [Next Hop]
```
---
### RIP Routing
#### RIP enable
```console
(config)#router rip
(config-router)#version 2
(config-router)#no auto-summary
```
#### NW zu RIP hinzufügen
```console
(config)#router rip
(config-router)#network 10.45.10.0 … NW Adresse
```
#### Default Routen weitergeben
---
```console
(config)#router rip
(config-router)#default-information originate 
```

#### Default Routen weitergeben (IPv6 RIP)
---
```console
(config)#interface [Interface]
(config-if)#ipv6 rip <NAME> default-information originate
(config-if)#ipv6 rip <NAME> default-information only
```

Wenn `originate` gesetzt ist, erhalten die anderen Router alle bekannten Routen des sendenden Routers.
Mit `only` erhalten die anderen Router nur die Default-Route.

#### Passive Interface
```console
(config-router)#passive-interface g0/0
```

#### Redistribute OSPF into RIP

```console
router rip
 version 2
 no auto-summary
 redistribute ospf 1 metric 2
```
---
### OSPF Routing
#### OSPF enable
```console
(config)#router ospf 1 oder (config)#router ospfv3
(config-router)#no auto-summary
```
#### OSPFv3
---
```console
(config)#ipv6 router ospf 10
(config-rtr)#router-id 1.1.1.1
(config-rtr)#exit
(config)#interface GigabitEthernet0/0
(config-if)#ipv6 ospf 10 area 1
(config)#interface Serial0/0/0
(config-if)#ipv6 ospf 10 area 0
(config-if)#end
#
```
#### Default Routen weitergeben
---
```console
(config)#router ospf 1
(config-router)#default-information originate 
```
#### NW zu OSPF hinzufügen
```console
(config-router)#network NetzwerkIP Wildcardmask area [Zahl] z.B
(config-router)#network 192.168.10.0 0.0.0.255 area 0
```
#### Passiv Interface
```console
(config-router)#passive-interface g0/0
```

#### Von Broadcast zu Point-zu-Point wechseln
```console
interface GigabitEthernet 0/0/0
ip ospf network point-to-point
```
#### Redistribute RIP into OSPF
```console
router ospf 1
 redistribute rip subnets
```
### Basic BGP Configuration

```console
router bgp 200
 bgp log-neighbor-changes
 neighbor 10.10.10.10 remote-as 300
 network 203.0.113.0 mask 255.255.255.0
 aggregate-address 203.0.0.0 254.0.0.0 as-set summary-only
 no auto-summary
```
#### Local Pref/ Next Hop Self
Wichtig für IBGP
```console
router bgp 100
 no synchronization
 bgp default local-preference 150
 bgp log-neighbor-changes
 neighbor 7.0.0.254 remote-as 100
 neighbor 7.0.0.254 next-hop-self
 no auto-summary
 ```

 #### Metric
 ```console
 router bgp 100
 no synchronization
 bgp log-neighbor-changes
 network 105.0.1.0 mask 255.255.255.0
 neighbor 5.0.0.253 remote-as 100
 neighbor 5.0.0.253 route-map SETMEDOUT out
 neighbor 6.0.0.253 remote-as 300
 neighbor 6.0.0.253 route-map SETMEDOUT6 out
 neighbor 8.0.0.254 remote-as 100
 no auto-summary

route-map SETMEDOUT permit 10
 set metric 50
route-map SETMEDOUT6 permit 20
 set metric 70
 ```

 #### Weight
 ```console
 router bgp 200
 neighbor 2.0.0.254 remote-as 100
 neighbor 2.0.0.254 weight 200
 neighbor 4.0.0.253 remote-as 300
 neighbor 4.0.0.253 weight 250
 no auto-summary
```
Restart the BGP routes
```console
 do clear ip bgp * soft
 ```

#### Equal Load Balancing
```console
router bgp 100
 maximum-paths ibgp 2
 no auto-summary
 ```
#### Unequal Load Balancing
change to 1:4 for 6.0.0.0 and 3.0.0.0

for network 6.0.0.0 on f0/1 set bandwitdth 10000
for network 3.0.0.0 on f2/0 set bandwitdth 40000

```console
int f0/1
bandwidth 10000
int f2/0
bandwidth 40000
```
use bandwith in bgp config:

```console
router bgp 300
 bgp dmzlink-bw
 neighbor 3.0.0.254 remote-as 100
 neighbor 3.0.0.254 dmzlink-bw
 neighbor 6.0.0.254 remote-as 100
 neighbor 6.0.0.254 dmzlink-bw
 maximum-paths 2
 ```

#### Default Route
```console
ip route 0.0.0.0 0.0.0.0 10.10.10.2
network 0.0.0.0
```

#### Test BGP
```console
show bgp
show ip router
```

---
### Access Listen - Standard
#### Access List erstellen
```console
(config)#access-list {List-ID} remark {Kommentar}
(config)#access-list {List-ID} [permit | deny] {IP} {Wildcard}
#Um alle zu erlauben:
permit 0.0.0.0 255.255.255.255 

```
#### Access List Einträge hinzufügen
```console
(config)#ip access-list standard {ACL-Name}
(config-std-nacl)#{Eintrag ID} [permit | deny] {IP-Adresse} {Wildcard}
```
#### Access Lists Matches clearen
```console
#clear access-list counter {ACL-Name}
```
#### Access Lists Interface zuweisen
```console
(config-if)#ip access-group {access-list-numer | access-list-name} {in | out}3
```


---
### Access Listen - Extended

### Access List erstellen und Einträge hinzufügen
```console
(config)#ip access-list extended {ACL-Name}
(config-ext-nacl)#{Eintrag ID} [permit | deny] {Protokoll} {Quell-IP} {Wildcard} {Ziel-IP} {Wildcard} [eq {Port}]
```
### Access List auf Interface zuweisen
```console
Router(config)#int {Interface}
Router(config-if)#ip access-group {ACL-Name} {in | out}
```
### Acces List löschen
```console
no ip access-list extended {ACL-Name}
```
---
### VLAN
#### Subinterfaces
```console
(config)#interface gigabitEthernet 0/1.50
(config-subif)#encapsulation dot1Q 50 
(config-subif)#ip address [IP] [Subnet]
```
---
### Etherchannel
#### Portchannel
```console
(config)#port-channel load-balance [dst/src/dst-src]-ip

(config)#interface range {Interface} - {Interface}
(config-if)#channel-protocol {Protocol} lacp
(config-if)#channel-group {Gruppe} mode active
(config)#interface port-channel {Gruppe}
(config-if)#switchport trunk allowed vlan {VLANID,VLANID,VLANID}
(config-if)#switchport trunk native vlan {VLANID}
(config-if)#switchport trunk encapsulation dot1q
(config-if)#switchport mode {Mode}
```
---
### HSRP

Version
```console
standby version 2
```
Groups
```console
standby <group-number> ip <ip address>
```
priority settings
```console
standby <group-number> priority <value>
```
activate preemtion function
```console
standby <group-number> preempt
```
WAN interface
```console
standby <group-number> track
```
### VRRP

Groups
```console
vrrp <group-number> ip <ip address>
```
priority settings
```console
vrrp <group-number> priority <value>
```

Tracking interface
```console
track <track id> interface <WAN interface> line-protocol
vrrp <group-number> track <track id> decrement <value>
```
---
## Switch-Config
---
### VLAN
#### VLAN erstellen
```console
(config)#vlan [VLAN-ID]
(config-vlan)#name [VLAN-Name]
```
#### Ein VLAN löschen
```console
(config)#no vlan [VLAN-ID]
```
#### Alles VLANs löschen
```console
(config)#delete flash:vlan.dat
```
#### VLAN Interface(Access) zusweisen
```console
(config)#interface [InterfaceID]
(config-if)#switchport mode access
(config-if)#switchport access vlan [VLAN-ID]
```
#### VLAN Interface(Trunk) zuweisen
> Note: The need for "encapsulation dot1q" is dependend on the device and may not exist, Cisco uses this by default 
```console
(config)#interface [InterfaceID]
(config-if)#switchport trunk encapsulation dot1q
(config-if)#switchport mode trunk
(config-if)#switchport trunk native vlan [VLAN-ID]
(config-if)#switchport trunk allowed vlan [VLAN-List] //Switchporttrunk allowed vlan 10,20,30,99
```
Validation of port status
```console
show interfaces Po1 switchport
```
### VLAN Layer 3 Switch Routing
#### VLAN Interfaces erstellen
```console
(config)#interface vlan 50
(config-if)#ip address [IP] [Subnet]
```
#### Routing einschalten
```console
(config)#ip routing
```
---
### STP Spanning-Tree
#### Interface Spanning-Tree
```console
(config-if)#spanning-tree portfast mode
```
#### Spanning-Tree aktivieren
```console
(config)#spanning-tree vlan vlan-id
```
#### Spanning-Tree deaktivieren
```console
(config)#no spanning-tree vlan vlan-id
```
#### Root Guard
```console
(config)#interface fastEthernet 0/1
(config-if)#spanning-tree rootguard
```
#### BPDU Guard
```console
(config-if)#spanning-tree portfast
(config)#spanning-tree portfast bpduguard
```
#### BPDU Filtering 1 Port
```console
(config-if)#spanning-tree bpdufilter enable
```
#### BPDU Filtering all Ports
```console
(config)#spanning-tree portfast bpdufilter default
```
---
#### Port-Security
```

```
---
### VTP
#### VTP Modes
```console
(config)#vtp domain {Domain-name}
(config)#vtp mode {server} / {client} / {transparent}
(config)#vtp version {dont need}
(config)#vtp password {password}
```
---
### Router & Switch Config
#### SNMP Read Only
```console
(config)#snmp-server community public RO
```
#### SNMP Write
```console
(config)#snmp-server community private RW 
```
