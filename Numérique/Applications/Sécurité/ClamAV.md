---
title: ClamAV
description: 
published: true
date: 2024-06-06T17:25:14.544Z
tags: 
editor: markdown
dateCreated: 2024-06-06T17:25:14.544Z
---

# ClamAV

ClamAV is an open source anti-virus.

<https://www.clamav.net/>

## Commandes

### Update signatures

```bash
freshclam
```
Service `clamav-freshclam.service` too.

### Background service

Start and enable `clamav-daemon.service` service.

## External definitions

### fangfrisch

<https://rseichter.github.io/fangfrisch/>

`/etc/fangfrisch/fangfrisch.conf`


```bash
sudo -u clamav /usr/bin/fangfrisch --conf /etc/fangfrisch/fangfrisch.conf initdb
```

## Ressources

- <https://wiki.gentoo.org/wiki/ClamAV>
- <https://sebsauvage.net/wiki/doku.php?id=clamav>
- <https://wiki.archlinux.org/title/ClamAV>
