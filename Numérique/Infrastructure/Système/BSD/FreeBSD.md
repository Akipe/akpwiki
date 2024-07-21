---
title: FreeBSD
description: 
published: true
date: 2024-07-21T19:19:42.680Z
tags: 
editor: markdown
dateCreated: 2024-05-21T11:40:23.220Z
---

# FreeBSD

## Installation

### Microcode

- <https://www.thomas-krenn.com/en/wiki/Update_Intel_Microcode_on_FreeBSD>

```shell
pkg update
pkg install cpu-microcode
pkg install devcpu-data

echo 'microcode_update_enable="YES"' >> /etc/rc.conf

service microcode_update start
```

```conf
# /boot/loader.conf
cpu_microcode_load="YES"
cpu_microcode_name="/boot/firmware/intel-ucode.bin"
```

Reboot.

## Configuration

### Lister les paramètres

```shell
sysctl -a
sysctl -a | grep rss
```
