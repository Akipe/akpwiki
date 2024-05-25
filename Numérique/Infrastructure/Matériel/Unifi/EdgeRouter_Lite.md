---
title: EdgeRouter Lite
description: 
published: true
date: 2024-05-25T14:51:24.692Z
tags: 
editor: markdown
dateCreated: 2024-05-25T14:04:13.454Z
---

# EdgeRouter Lite

- <https://www.forshee.me/ubiquiti-edgerouter-lite-setup-part-1-the-basics/>

## Configuration

### Réinitialiser

<https://help.ui.com/hc/en-us/articles/205202620-EdgeRouter-Reset-to-Factory-Defaults>

- Materiel : "Clears all configuration and system files, resetting the device to the factory default state."
- Logiciel : "Only clears the configuration and leaves the other system files intact."

> User Tip: Usernames and passwords are stored in the configuration file. Using either reset methods will clear the configuration.

Identifiants par défaut :

> Identifiant et mot de passe : *ubnt*

#### Matériel

The hardware reset is done using the physical reset button and can be done using either method below.

##### Runtime

> Runtime Reset Factory reset while the device is running/operational.

1. Press and hold the reset button.
2. The port LEDs will start light up in sequence starting from port 1 and ending at the last port.
3. Continue holding the reset button for approximately 10 seconds until the LED on port 1 lights up again.
4. Release the reset button.
5. The EdgeRouter will reboot.
6. Wait for the reboot to complete.
7. Connect to the eth0 port and manage the device by opening a browser and navigating to the https://192.168.1.1 default IP address.

##### Power On

> Power On Reset Factory reset while powering on the device by plugging in the power cable.

1. Disconnect the power cord from the EdgeRouter.
2. While reconnecting the power cord to the EdgeRouter, press and hold the reset button.
3. The port LEDs will start light up in sequence starting from port 1 and ending at the last port.
4. Continue holding the reset button for approximately 10 seconds until the LED on port 1 lights up again.
5. Release the reset button.
6. The EdgeRouter will reboot.
7. Wait for the reboot to complete.
---

8. Connect to the eth0 port and manage the device by opening a browser and navigating to the https://192.168.1.1 default IP address.

#### Logiciel

##### Web UI

Depuis l'interface web.

##### Terminal

```shell
sudo cp /opt/vyatta/etc/config.boot.default /config/config.boot
reboot
```

### DNS

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

### Hardware Offloading

- <https://help.ui.com/hc/en-us/articles/115006567467-EdgeRouter-Hardware-Offloading>

#### Informations

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

#### Activer

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

### UPNP

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

### Wireguard

- <https://github.com/WireGuard/wireguard-vyatta-ubnt/wiki/EdgeOS-and-Unifi-Gateway>

### Add Debian packages

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

### Autre

```shell
set service gui older-ciphers disable
```
