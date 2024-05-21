---
title: OpenWRT
description: 
published: true
date: 2024-05-21T11:21:01.050Z
tags: 
editor: markdown
dateCreated: 2024-05-21T11:21:01.050Z
---

# OpenWRT

## Package manager

### Upgrade all packages

```bash
opkg list-upgradable | cut -f 1 -d ' ' | xargs -r opkg upgrade  
```

## UCI

How to save config :

```bash
uci commit network
/etc/init.d/network restart
```

## Luci

### Enable HTTPS web admin

By default HTTPS is available with OpenWRT 21.02.

To enable redirection :

```bash
uci set uhttpd.main.redirect_https=1     # 1 to enable redirect, 0 to disable redirect
uci commit uhttpd
service uhttpd reload
```

## Network

### DHCP Client

```bash
uci set network.lan.proto="dhcp"

uci commit network
/etc/init.d/network restart
```

### Manual IP

```bash
uci set network.lan.proto="static"
uci set network.lan.ipaddr="192.168.1.2"
uci set network.lan.netmask="255.255.255.0"
uci set network.lan.gateway="192.168.1.1"
uci set network.lan.dns="192.168.1.1"

uci commit network
/etc/init.d/network restart
```

## Guest agent

Need install `qemu-ga` package.

## Optimization

### Cryptographic acceleration

Check what is supported:

```bash
cat /proc/crypto
openssl engine -t -c
```

#### Cryptodev

```bash
kmod-cryptodev
(libopenssl-devcrypto)
(libopenssl-afalg)
```

#### AF_ALG

```bash
kmod-crypto-user
(libopenssl-afalg_sync)
```