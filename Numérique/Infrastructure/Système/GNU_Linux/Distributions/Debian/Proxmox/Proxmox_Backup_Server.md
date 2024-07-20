---
title: Proxmox Backup Server
description: 
published: true
date: 2024-07-20T14:59:52.657Z
tags: 
editor: markdown
dateCreated: 2024-07-20T13:56:28.149Z
---

# Proxmox Backup Server

## Information

### Afficher l'empreinte du certificat

```shell
proxmox-backup-manager cert info |grep Fingerprint
```

## Configuration

### Montage d'un datatstore en CIFS

Voir [Mount](/Numérique/Infrastructure/Système/GNU_Linux/Mount#fstab)

Pour définir le `uid` et le `gid`, on récupére la valeur de la commande `id backup`.

```fstab
//SERVER/SHARENAME /mnt/MOUNTPOINT cifs _netdev,nofail,iocharset=utf8,credentials=/etc/samba/credentials/share,x-systemd.automount,uid=34,noforceuid,gid=34,noforcegid 0 0
```

Créer en terminal de datastore à la main :

```shell
proxmox-backup-manager datastore create NAME /mnt/tl-cifs/dest
```

## Ressources

### Documentation

- <https://pbs.proxmox.com/docs/index.html>
- <https://pbs.proxmox.com/wiki/>
