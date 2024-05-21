---
title: Bouygue Telecom
description: 
published: true
date: 2024-05-21T19:53:35.742Z
tags: 
editor: markdown
dateCreated: 2024-05-21T19:53:35.742Z
---

# Bouygue Telecom

## Remplacer la Box

- <https://lafibre.info/remplacer-bbox/>
- <https://lafibre.info/remplacer-bbox/aide-pour-la-delegation-de-prefixe-ipv6/>
- <https://lafibre.info/remplacer-bbox/retro-ingenierie/>
- <https://lafibre.info/remplacer-bbox/aide-pour-la-delegation-de-prefixe-ipv6/>
- <https://lafibre.info/remplacer-bbox/configurer-lipv6-sur-les-edge-router-chez-bouygues-telecom/>
- <https://lafibre.info/remplacer-bbox/aide-pour-la-delegation-de-prefixe-ipv6/>
- <https://lafibre.info/remplacer-bbox/edgerouter-4-le-flux-tv-coupe-au-bout-de-5-minutes/>
- <https://lafibre.info/remplacer-bbox/edge-router-ouverture-des-ports-ipv6-ne-fonctionne-pas-ipv4-ok/>
- <https://lafibre.info/remplacer-bbox/remplacement-bbox-unifi-par-edgerouter-x-sfp/>
- <https://lafibre.info/remplacer-bbox/ftth-remplacer-sa-bbox-par-un-edgerouter-x-er-x-tuto-et-tests-de-debits/>
- <https://routeur4g.fr/discussions/discussion/1230/retour-experience-b715s-edgerouter-vpn>
- <https://forum.nextinpact.com/topic/174169-monter-son-propre-routeur-fibre-opnsense/>
- <https://lafibre.info/remplacer-bbox/aide-pour-la-delegation-de-prefixe-ipv6/>

### Edgerouter

```
ethernet eth1 {
     duplex auto
     speed auto
     vif 100 {
         address dhcp
         description "eth1.100 ONT ByTel"
         dhcp-options {
             client-option "send vendor-class-identifier &quot;BYGTELIAD&quot;;"
             default-route update
             default-route-distance 210
             name-server update
         }
         dhcpv6-pd {
             duid 00:03:00:01:XX:XX:XX:XX:XX:XX // Mac Bbox
             pd 0 {
                 interface eth0 { //Ici, je délègue le premier /64 dispo dans le /60 qui m'est assigné et je mets ::ffff comme adresse à l'interface eth0 de mon routeur (LAN)
                     host-address ::ffff
                     prefix-id :0
                 }
                 prefix-length /60
             }
             prefix-only
             rapid-commit disable
         }
         firewall {
             in {
                 ipv6-name WANv6_IN
                 name WAN_IN
             }
             local {
                 ipv6-name WANv6_LOCAL
                 name WAN_LOCAL
             }
         }
         mac XX:XX:XX:XX:XX:XX //Mac Bbox
     }
 }
```

```
eth0.100 & eth1 dup-addr-detect-transmits 1 
```

```
set interfaces ethernet eth0 vif 100 dhcp-options client-option "send vendor-class-identifier &quot;BYGTELIAD&quot;;"
set interfaces ethernet eth0 mac <MAC BBOX>
set interfaces ethernet eth0 vif 100 mac <MAC BBOX>
```

```
show interfaces
```

#### IPv6

- https://blog.daknob.net/setting-up-edgemax-devices-for-ote-ipv6/
- https://help.ui.com/hc/en-us/articles/115002531728-EdgeRouter-Beginners-Guide-to-EdgeRouter
- https://www.reddit.com/r/Ubiquiti/comments/j8ooab/how_do_i_enable_ipv6_on_an_edgerouter_lite/
- https://gist.github.com/dmtucker/cf3f241cf002367825633c988ff19fcf
- https://help.pentanet.com.au/hc/en-us/articles/4403292092307-IPv6-configuration-on-Ubiquiti-Edgerouters
- https://davidwesterfield.net/2020/06/edgerouter-4-ipv6-setup/
- https://davidwesterfield.net/2021/03/enabling-ipv6-prefix-delegation-on-att-internet-for-a-second-firewall/

```
edit firewall ipv6-name WANv6_IN
set default-action drop
set rule 10 description "Accept Established/Related"
set rule 10 action accept
set rule 10 protocol all
set rule 10 state established enable
set rule 10 state related enable
set rule 20 description "Drop invalid state"
set rule 20 protocol all
set rule 20 state invalid enable
set rule 20 action drop
set rule 30 description "Accept ICMPv6"
set rule 30 action accept
set rule 30 protocol icmpv6
top
edit firewall ipv6-name WANv6_LOCAL
set default-action drop
set rule 10 description "Accept Established/Related"
set rule 10 action accept
set rule 10 protocol all
set rule 10 state established enable
set rule 10 state related enable
set rule 20 description "Drop invalid packets"
set rule 20 protocol all
set rule 20 state invalid enable
set rule 20 action drop
set rule 30 description "Accept ICMPv6"
set rule 30 action accept
set rule 30 protocol icmpv6
set rule 40 description "Accept DHCP"
set rule 40 action accept
set rule 40 protocol udp
set rule 40 destination port 546
set rule 40 source port 547
top
edit firewall ipv6-name LANv6_LOCAL
set rule 30 description "Accept ICMPv6"
set rule 30 action accept
set rule 30 protocol icmpv6
top
edit firewall ipv6-name LANv6_IN
set rule 30 description "Accept ICMPv6"
set rule 30 action accept
set rule 30 protocol icmpv6
top





set rule 31 description "Accept ICMPv6 packet-too-big"
set rule 31 action accept
set rule 31 protocol icmpv6
set rule 31 icmpv6 type packet-too-big
set rule 32 description "Accept ICMPv6 time-exceeded"
set rule 32 action accept
set rule 32 protocol icmpv6
set rule 32 icmpv6 type time-exceeded
set rule 33 description "Accept ICMPv6 parameter-problem"
set rule 33 action accept
set rule 33 protocol icmpv6
set rule 33 icmpv6 type parameter-problem
set rule 34 description "Accept ICMPv6 echo-request"
set rule 34 action accept
set rule 34 protocol icmpv6
set rule 34 icmpv6 type echo-request
set rule 35 description "Accept ICMPv6 destination-unreachable"
set rule 35 action accept
set rule 35 protocol icmpv6
set rule 35 icmpv6 type destination-unreachable
```