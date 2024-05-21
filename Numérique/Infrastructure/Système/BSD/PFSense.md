---
title: PFSense
description: 
published: true
date: 2024-05-21T19:09:34.108Z
tags: 
editor: markdown
dateCreated: 2024-05-21T19:09:34.108Z
---

# PFSense

- https://tutox.fr/2022/03/26/debugger-une-regle-de-parefeu-pfsense/
- https://www.provya.net/?d=2023/06/22/10/04/30-pfsense-je-nai-plus-acces-a-mon-firewall-comment-faire

## Informations

## Installation

### Identifiants par défaut

Identifiants :

```
admin
```

Mot de passe :

```
pfsense
```

## Configuration

### Après installation

#### Advanced

-  TCP port : 4443
-  Enable Secure Shell + port 2222
- enable Serial Terminal
- Primary Console : VGA console
- ? Console menu Password protect the console menu

-  Firewall Optimization Options : conservative

- Bogon Networks  Update Frequency  : weekly

-  NAT Reflection mode for port forwards : pure nat
-  Automatic create outbound NAT rules that direct traffic back out to the same subnet it originated from.

-   DHCP6 DUID : DUID-UUID

- enable all offloading

- PowerD enable
- hiadaptive

- cryptographic hardware : aes-ni & bsd crypt device
- thermal sensors : intel

-  Kernel PTI : enable
-  MSD mode : mitigation disabled

-  Use RAM Disks: enable
-   RAM Disk tmp : 500
-   RAM disk var : 1000
-   Periodic ram disk data backups : 1 1 1 1
- netgate device id : do not send netgate deivce id with user agent

#### General setup

- hostname : asn-octopus
- domaine : domaine.lan
- dns server
- timeservers : fr.pool.ntp.org
- theme : pfsense-dark
- hostname in menu : fully qualified domaine name

#### Firewall

##### Nat

###### Outbound

- Automatic outbound Nat : save

#### Services

##### DHCPv6 Server

###### LAN

DHCPv6 server

- enable

Router adverstisement

- router mode : assisted

##### DNS Resolver

General sesstings

- Register DHCP leases in the DNS Resolver
- Register DHCP static mappings in the DNS Resolver
- Register connected OpenVPN clients in the DNS Resolver

Advance settings

- Prefetch Support
- Prefetch DNS Key Support

##### NTP

Settings
- time servers : 0.fr.pool.ntp.org, 1.fr ...

##### UPNP & NAT PMP

- enable
- Allow UPnP Port Mapping
- Allow NAT-PMP Port Mapping
- Log packets handled by UPnP & NAT-PMP rules.

#### User manager

- create a new admin user
- disable "admin" user

## FDN VPN

### Certificate Manager / CA

- FDN VPN CA ( contient tout)
- import an existing certificate authority
-  Trust Store
Add this Certificate Authority to the Operating System Trust Store

- puis faire la même chose mais par certificat :
  - FDN VPN CA Cert Signing 2033 (premier)
  - FDN VPN CA Cert Signing 2021 (deuxieme)
  - FDN VPN CA FDN (troisieme)

- Certificate data : contente "ca-vpn-fdn.crt"

### OpenVPN / Clients / Add

- Description : FDN_VPN

- Server mode : Peer to peer (SSL/TLS)
- Device mode : tun

- Protocol : (UDP IPv4 & IPv6)
- Server host or address : vpn.fdn.fr
- server port : 1194

- username & password : voir FDN

- désactiver TLS configuration
- peer certificate authority : FDN VPN CA
- Client Certificate : None
- Data Encryption Negotiation : enable
- Date encryption algorithms : AES-256-GCM / AES-128-GCM
- fallback data encryption : AES-256-gcm (?AES-256-cbc)
- auth digest algorithm : SHA256
- hardware crypto : (/dev/crypto engine) : enable AES-NI si dispo!
- Server Certificate Key Usage Validation : Enforce key usage disable

- IPv4 Tunnel network : un reseau IPv4 (ex: 10.0.8.0/24)
- IPv6 Tunnel network : un reseau IPv4 (ex: fd35:93d4:bf5e::/64)
- IPv4 Remote network(s) : votre réseau IPv4 LAN (ex: 192.168.100.0/24)
- IPv6 Remote network(s) :

- Don't pull routes : enable
- Don't add/remove routes : enable

- (UDP Fast I/O : Enable)
- (Send/Receive Buffer : 2.00MiB)
- Gateway creation : Both

- (Verbosity level : 3 or 0)

### Interfaces / Interface Assignments

add ovpnv1 ; save

Click OPTX -> description : WAN_FDN

Block private networks and loopback addresses non coché
Block bogon networks non coché

Puis reappliquer les paramètre OpenVPN pour relancer l'acquisition des IPs.

### System Routing Gateways

Default gateway IPv4 : votre current WAN : WAN_DHCP
Default gateway IPv6 : votre current WAN : WAN_DHCP6

### Firewall NAT Outbound

- Outbound NAT Mode : Hybrid Outbound NAT rule generation.
(Automatic Outbound NAT + rules below)
- mappings : add new one :
  - Interface : WAN_FDN
  - Address Family : IPv4+IPv6 (ipv4 only?)
  - Source : vos différents LAN qui vont utiliser le VPN : 192.168.100.1/24
  - Description : LAN to WAN_FDN VPN
- dupliquer cette rule pour protocole ISAKMP :
  - destination : port or range 500
  - desciption : LAN to WAN_FDN VPN for ISAKMP
- apply

### Firewall Rules LAN

- add fleche haut
  - action : pass
  - interface : lan
  - address family : IPv4
  - protocol : any
  - Source : LAN net
  - Description : Route LAN IPv4 to WAN_FDN VPN
  -  Advanced Options :
    -  (Tag : FDN_VPN_ONLY) pour kill switch
    - Gateway : WAN_FDN_VPNV4
- copy for IPv6 :
  - Address Family : IPv6
  - Description : Route LAN IPv4 to WAN_FDN VPN
  -  Advanced Options :
    -  Gateway : WAN_FDN_VPNV6
-  pour kill switch : Floating RULES :
  -  add one :
    -  Action block
    - Interface : WAN
     - Address Family : IPv4+IPv6
    - Direction : any
     - Protocol : any
     - Advanced Options :
       - Tagged : FDN_VPN_ONLY
   - Description : Kill switch for blocking internet access without FDN VPN

### LAN (IPv6)

-  IPv6 Configuration Type : static IPv6
-  IPv6 address : xxxx:xxxx:xxxx::1 / 64 (voir la config FDN)
-  apply

#### Services DHCPv6 Server & RA LAN DHCPv6 Server

- DHCPv6 Server
  - enavle DHCPv6 server on interface lan
  - range : xxxx.d::1000 to xxxx.d::2000
- Router Advertisements
  - Router mode : assisted


### pb routage

```
redirect-gateway def1
route 10.0.0.0 255.0.0.0 net_gateway
route 172.16.0.0 255.240.0.0 net_gateway
route 192.168.0.0 255.255.0.0 net_gateway
route-ipv6 ::/1
route-ipv6 8000::/1
```

## fix

- https://forum.netgate.com/topic/161208/openvpn-2-5-0-certificate-verification-fails/27
- https://redmine.pfsense.org/issues/4521