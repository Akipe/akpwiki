---
title: Commande utile
description: 
published: true
date: 2024-03-04T12:28:30.095Z
tags: 
editor: markdown
dateCreated: 2024-03-04T12:28:30.095Z
---

# Commande utile

# Helper shell

### Observer une commande & rafraichir
`watch cat /un/path`

# Réseau

### Trouver process qui utilise un port
```
sudo netstat -nlp | grep :80
```

# Fichiers

## Information
`stat nom_fichier.txt`
`file nom_fichier.txt`

## Backup
```
rsync -av --stats --progress /dir/source /dir/dest
  --no-perms --no-owner --no-group # Not copy ownership and permission
```

# Erreurs / Debug


## REISUB - the gentle Linux restart

According to Lifehacker a frozen Linux system that's not responding to the Ctrl-Alt-Delete three-finger-salute can be restarted more safely than by pushing the power button, which is usually the next step.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB will get you safely restarted. REISUO will do a shutdown rather than a restart.

Sounds like either an April Fools joke or some very strange magic akin to the old BIOS beeps we used to use to diagnose PC faults so bad that nothing would boot. Wikipedia comes to the rescue with an in-depth listing of all the SysRq keys.

    R: Switch the keyboard from raw mode to XLATE mode
    E: Send the SIGTERM signal to all processes except init
    I: Send the SIGKILL signal to all processes except init
    S: Sync all mounted filesystems
    U: Remount all mounted filesystems in read-only mode
    B: Immediately reboot the system, without unmounting partitions or syncing


# Informations

## Informations sur la distribution

```
uname -a # Kernel
cat /proc/version
lsb_release -a # Distribution, or
cat /etc/*-release
hostnamectl
```

# Distributions

## Archlinux

### Fixer les signatures invalides
```
sudo pacman -S archlinux-keyring
```

### Lister les paquet qui ne sont pas dans les repos
```
pacman -Qm
```

### "Failed to commit transaction (invalid or corrupted package)" error
```
find /var/cache/pacman/pkg/ -iname "*.part" -delete
```


### Relancer une mise à jour des sites mirroires repo
```
sudo systemctl start reflector.service
```


### ripgrep
> Rechercher de manière recursive dans les fichiers
`rg "text à chercher"`

### jq
> Manipuler du JSON en shell
`jq`

### tree
> Afficher l'arborecance des fichiers/dossiers
`tree`

> Lister uniquement les dossiers
`tree -d`

### bat
> Cat clone with syntax highlighting and git integration
https://github.com/sharkdp/bat
`bat README.md`


## Network

### DNS
> Supprimer le cache DNS
```
systemctl is-active systemd-resolved
sudo systemd-resolve --flush-caches
systemd-resolve --statistics
```