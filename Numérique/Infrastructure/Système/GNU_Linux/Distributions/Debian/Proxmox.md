---
title: Proxmox
description: 
published: true
date: 2024-07-19T17:29:35.407Z
tags: 
editor: markdown
dateCreated: 2024-07-19T17:23:48.143Z
---

# Proxmox

## Host

### Configuration

#### Changement du hostname

Changer les fichiers suivants :

- `/etc/hosts`
- `/etc/hostname`
- `/etc/mailname`
- `/etc/postfix/main.cf`

#### Définir le VLAN

Par exemple pour le VLAN *100* et pour l'appareil *enp2* :

```conf
# /etc/network/interfaces

# ...
auto vmbr0
iface vmbr0 inet static
        bridge-ports enp2 # A changer
        bridge-stp off
        bridge-fd 0
        bridge-vlan-aware yes
        bridge-vids 2-4094

auto vmbr0.100 # Définir le VLAN, par exemple à 100
iface vmbr0.100 inet static
        address 10.0.0.100/24
        gateway 10.0.0.1
# ...
```