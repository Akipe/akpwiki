---
title: Windows 11
description: 
published: true
date: 2024-04-21T15:16:04.934Z
tags: 
editor: markdown
dateCreated: 2024-04-21T15:16:04.934Z
---

# Windows 11

## Installation

### Vérification des pré-requis

#### WhyNotWin11

<https://github.com/rcmaehl/WhyNotWin11>

#### Éviter le compte Microsoft

<https://www.tutos-informatique.com/3-astuces-pour-installer-windows-11-sans-compte-microsoft/>

#### Désactiver les obligations

    Shift+F10 (run cmd)
    run regedit
    in HKEY_LOCAL_MACHINE\SYSTEM\Setup
    right-click New, Key, LabConfig
    New, DWORD (32-bit), BypassTPMCheck, 1
    same for BypassRAMCheck and BypassSecureBootCheck

#### Sans compte Microsoft

1. Follow the Windows 11 install process until you get to the "choose a country" screen.
2. Shift + F10
3. Type `OOBE\BYPASSNRO`
4. `Shift + F10` again, type `ipconfig /release` then enter

## Mise à jour

### Materiel incompatible

- <https://lecrabeinfo.net/windows-11-forcer-la-mise-a-jour-22h2-sur-un-pc-non-compatible.html>
- <https://www.tech2tech.fr/mettre-a-jour-vers-windows-11-sans-puce-tpm/>
	- <https://github.com/CodeProf14/Fix-TPM/tree/main/Fix%20TPM>
- <https://jensd.be/1860/windows/upgrade-to-windows-11-22h2-on-unsupported-hardware>

## Configuration 

### Publicités

<https://lecrabeinfo.net/supprimer-les-publicites-dans-windows-11.html>

### Vie privée

<https://lecrabeinfo.net/supprimer-les-publicites-dans-windows-11.html#dans-les-donnees-de-diagnostic>

#### O&O ShutUp10++ 

<https://www.oo-software.com/fr/shutup10>