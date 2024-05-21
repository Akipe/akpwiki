---
title: OpenWRT
description: 
published: true
date: 2024-05-21T19:56:11.942Z
tags: 
editor: markdown
dateCreated: 2024-05-21T11:21:01.050Z
---

# OpenWRT

## Installation

- <https://downloads.openwrt.org/releases/>
- <https://downloads.openwrt.org/>
- <https://firmware-selector.openwrt.org/>

### Pour x86

- <https://firmware-selector.openwrt.org/?version=23.05.2&target=x86%2F64&id=generic>
- <https://teklager.se/en/knowledge-base/openwrt-installation-instructions/>

## Mise à jour

- <https://forum.openwrt.org/t/sysupgrade-help-for-x86-64/112043/14>
- <https://sysupgrade.openwrt.org/>
- <https://openwrt.org/docs/guide-user/installation/openwrt_x86#upgrading>

```
If you had used a **ext4-combined.img.gz** type of image to install, there are 4 options for upgrading:

1. Write a new **ext4-combined.img.gz** image: this is the simplest option and is identical to first installation: all data, configs, packages and extra partitions will be wiped and you'll have a brand new OpenWrt system with default packages and configs. Then you can reinstall all packages and copy config files back and create extra partitions.
2. Use **sysupgrade**: this is default upgrading procedure, but the least recommended option for x86 machines. Proceed to [Sysupgrade](https://openwrt.org/docs/guide-user/installation/installation_methods/sysupgrade) for details.
3. Extracting boot partition image from **ext4-combined.img.gz** and writing it and **ext4-rootfs.img.gz**, leaving MBR partition table intact.
4. Extracting boot partition image from **ext4-combined.img.gz** and writing it, then uncompressing **rootfs.tar.gz** to existing rootfs partition.
```

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