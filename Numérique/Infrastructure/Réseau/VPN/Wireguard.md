---
title: Wireguard
description: 
published: true
date: 2024-06-06T16:38:01.154Z
tags: 
editor: markdown
dateCreated: 2024-06-06T16:38:01.154Z
---

# Wireguard

<https://wiki.salo.pe/vpn/wireguard.html>

## Commandes

### Générer une clé privée et publique pour un host

```bash
wg genkey | tee peer_A.key | wg pubkey > peer_A.pub
```

### Générer clés partagés

## Débugurer

```shell
echo "module wireguard +p" | sudo tee /sys/kernel/debug/dynamic_debug/control
```

Afficher les logs :

```shell
sudo dmesg -wT
```

désactiver :

```shell
echo "module wireguard -p" | sudo tee /sys/kernel/debug/dynamic_debug/control
```

## route

```shell
ip route add IP_VPN_SERVER via 192.168.1.1 dev enp4s0
```

## Outils

- Firezone : <https://github.com/firezone/firezone> & <https://www.firezone.dev/>