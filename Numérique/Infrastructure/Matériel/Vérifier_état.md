---
title: Vérifier l'état d'appareils
description: 
published: true
date: 2024-04-13T13:52:53.135Z
tags: 
editor: markdown
dateCreated: 2024-04-13T13:52:26.520Z
---

# Vérifier l'état d'appareils

## Périphériques externes

### Clés USB

- <https://www.cyberciti.biz/faq/linux-check-the-physical-health-of-a-usb-stick-flash-drive/>

(Sous GNU\Linux)

Vérifier la santé de la clé USB :

```shell
badblocks -w -s -o error.log /dev/sdX
```

- `-w` : Use write-mode test to scans for bad blocks by writing some patternson every block of the device, reading every block and comparing the contents.
- `-s` : Show the progress of the scan.
- `-o error.log` : Write the list of bad blocks to the error.log file in the current working directory.

Test de rapidité (avec l'application `f3`) :

```shell
# Test écriture
f3write /mnt/
# Test lecture
f3read /mnt/
```

Test de capacité (avec l'application `f3`) :

```shell
sudo ./f3probe --destructive --time-ops /dev/sdb
# Définir la taille correcte de l'appareil USB,
# Se servir de la commande précédante pour définir "--last-sec"
sudo ./f3fix --last-sec=16477878 /dev/sdb
```
