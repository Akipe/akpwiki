---
title: EdgeRouter Lite
description: 
published: true
date: 2024-05-25T14:04:13.454Z
tags: 
editor: markdown
dateCreated: 2024-05-25T14:04:13.454Z
---

# EdgeRouter Lite

- <https://www.forshee.me/ubiquiti-edgerouter-lite-setup-part-1-the-basics/>

### Configuration

#### DNS

- https://help.ui.com/hc/en-us/articles/115002673188-EdgeRouter-Using-dnsmasq-for-DHCP-Server
- https://help.ui.com/hc/en-us/articles/115010913367-EdgeRouter-DNS-Forwarding-Setup-and-Options
- https://github.com/cloudflare/cloudflared/issues/19
- https://www.justinho.com/blog/2020/09/03/cleanedgerouter.html
- https://www.reddit.com/r/Ubiquiti/comments/gnsc1g/reminder_dns_adblocker_malware_protection_for/

Pour pouvoir configurer :

```shell
configure
```

Puis

```shell
commit
```

Puis

```shell
save
```

#### Hardware Offloading

- <https://help.ui.com/hc/en-us/articles/115006567467-EdgeRouter-Hardware-Offloading>

##### Informations

```shell
show ubnt offload
```

```shell
show ubnt offload statistics
```

```shell
set system offload ipv4 table-size ?
set system offload ipv6 table-size ?
```

##### Activer

```shell
set system offload ipv4 forwarding enable
set system offload ipv4 gre enable
set system offload ipv4 pppoe enable
set system offload ipv4 vlan enable
set system offload ipv4 bonding enable

set system offload ipv6 forwarding enable
set system offload ipv6 pppoe enable
set system offload ipv6 vlan enable
set system offload ipv6 bonding enable

set system offload ipsec enable
```

```shell
set system offload ipv4 table-size ?
set system offload ipv6 table-size ?
```

#### UPNP

```shell
delete service upnp
delete service upnp2

set service upnp2 wan eth0.100
set service upnp2 listen-on eth1
set service upnp2 nat-pmp enable
```

```shell
clear upnp2 rules

configure

delete service upnp2

set service upnp2 wan eth0
set service upnp2 listen-on eth1
set service upnp2 listen-on eth2

set service upnp2 nat-pmp enable
set service upnp2 secure-mode enable

set service upnp2 acl rule 10 action deny
set service upnp2 acl rule 10 description "Deny Default Xbox Port 3074 to 192.168.1."
set service upnp2 acl rule 10 external-port 3074
set service upnp2 acl rule 10 local-port 0-65535
set service upnp2 acl rule 10 subnet 192.168.1.0/24

set service upnp2 acl rule 20 action deny
set service upnp2 acl rule 20 description "Deny Default Xbox Port 3074 to 192.168.2."
set service upnp2 acl rule 20 external-port 3074
set service upnp2 acl rule 20 local-port 0-65535
set service upnp2 acl rule 20 subnet 192.168.2.0/24

commit

save

exit
```

#### Wireguard

- <https://github.com/WireGuard/wireguard-vyatta-ubnt/wiki/EdgeOS-and-Unifi-Gateway>

#### Add Debian packages

- <https://help.ui.com/hc/en-us/articles/205202560-EdgeRouter-Add-Debian-Packages-to-EdgeOS>

```shell
configure
set system package repository stretch components 'main contrib non-free' 
set system package repository stretch distribution stretch
set system package repository stretch url http://http.us.debian.org/debian
commit ; save
```

Ensuite :

```shell
sudo apt-get update
```

**Ne JAMAIS utilisé la commande `apt-get upgrade` !!!**

#### Autre

```shell
set service gui older-ciphers disable
```
