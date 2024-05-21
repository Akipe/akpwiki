---
title: Fairphone 4
description: 
published: true
date: 2024-05-21T19:47:41.549Z
tags: 
editor: markdown
dateCreated: 2024-05-21T19:47:41.549Z
---

# Fairphone 4

## Distributions

### Guide

#### Mises en garde

##### Fonctionnalité anti-rollback

Caution: The FP4 comes with an anti-rollback feature. Google Android anti-roll back feature is supposedly a way to ensure you are running the latest software version, including the latest security patches.

If you try installing a version of /e/OS based on a previous AOSP core version than the one running on your phone, or based on a security patch that is older than the one on your device, you will brick your device.

To check the security patch level on your phone with a locked bootloader, prior to installing /e/OS, open your phone Settings » About Phone » Android Version » Android Security Patch Level.Then compare it against the level of the security patch on the /e/OS build as visible in the Downloads for the FP4 section below. 

> Example 1 :
> * Your FP4 with Google Android has a Security Patch Level saying June 5, 2022
> * The /e/OS build available says: /e/OS build : R stable (Security patch: 2022-05-05)
> * **In this example, the /e/OS build has an older Security Patch level than the origin, so the anti-roll back protection will trigger, and you will brick your phone**

> Example 2 :
> * Your FP4 with Google Android has a Security Patch Level saying June 5, 2022.
> * The /e/OS build available says: /e/OS build : R stable (Security patch: 2022-06-05)
> * **In this example, the /e/OS build has the same Security Patch level than the origin, so the anti-roll back protection will pass, and you will be able to install /e/OS with no issues.**

##### Blocage suite au relock

Faire la commande suivante :
```bash
fastboot flashing get_unlock_ability
```

Si le retours est :
- **0** : **NE PAS LOCK LE BOOTLOADER !** L'appareil ne sera plus utilisable sinon.
- **1** : le relock est possible.

#### Unlock bootloader

- <https://support.fairphone.com/hc/en-us/articles/10492476238865>
- <https://www.fairphone.com/en/bootloader-unlocking-code-for-fairphone-3/>
- <https://support.fairphone.com/hc/en-us/articles/18896094650513>

```shell
adb devices
adb reboot-bootloader
# Pour fp3
# fastboot oem unlock
fastboot flashing unlock
fastboot flashing unlock_critical
```

### Liste de Ditributions

#### Android

##### Fairphone OS

###### Téléchargement
<https://support.fairphone.com/hc/en-us/articles/4405858261777>

##### eOS
<https://doc.e.foundation/devices/FP4>

###### Téléchargement
- stable : <https://images.ecloud.global/stable/FP4/>
- dev : <https://images.ecloud.global/dev/FP4>

###### Installation
<https://doc.e.foundation/devices/FP4/install>

##### CalyOS
- Actualité : <https://calyxos.org/news/>
- Guide d'installation : <https://calyxos.org/install/devices/FP4/>
- Autre informations : <https://calyxos.org/docs/guide/fp4/>
- Mise à jour OTA : <https://calyxos.org/get/ota/>

## Astuces

### Démarrer la recovery

1. Débrancher le cable USB et éteindre le téléphone.
1. Retirer la batterie.
1. Remettre la batterie.
1. Rester appuyer sur le bouton `Augmenter Volume` jusqu'au démarrage du mode recovery.
1. Brancher le cable USB
1. Attendre le démarrage du mode recovery.

### Démarrer le bootloader

1. Débrancher le cable USB et éteindre le téléphone.
1. Retirer la batterie.
1. Remettre la batterie.
1. Rester appuyer sur le bouton `Diminuer Volume` jusqu'à l'arrive du menu du bootloader.
1. Brancher le cable USB
1. Attendre de l'arriver au menu du bootloader.

Également on peut passer par le mode recovery.
