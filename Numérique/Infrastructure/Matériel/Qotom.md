---
title: Qotom
description: 
published: true
date: 2024-03-04T12:57:59.666Z
tags: 
editor: markdown
dateCreated: 2024-03-04T12:57:59.666Z
---

# Qotom

## Bios

- <https://www.reddit.com/r/qotom/comments/kfz8zd/updating_bios_on_the_q335g4/>
- <https://www.qotom.net/faq/31.html>

### Mode bios ancien

### Mode UEFI

1. Préparer la clé USB
   - Formater la clé USB en FAT32
   - Décompresser le contenu de l'archive contenant le bios à mettre à jour sur la clé usb
   - Vérifier que le dossier `EFI` est bien présent
2. Mettre à jour le bios
   - Choisir la clé USB au boot
   - Taper `fs0:` puis `dir` et vérifier que c'est bien la clé usb (sinon essayé avec `fs1:`, etc)
   - Appuyer sur la lettre `F` puis `Entrer` pour démarrer le flash du bios

### Téléchargement

- <https://www.qotom.us/download/Bios/>

### Instruction installation

- <https://www.qotom.net/faq/31.html>

#### Q3XXG4-P

| Mini PC Model	| PCB Model	Version | CPU series | BIOS File Name | Update Time | Old BIOS File Name
|---|---|---|---|---|---
| Q300G4 | Q3XXG4-P	V1.0 | U | Q32BU200V10 | 2021-07-24 | Q3XXG405_10
| Q300G4 | Q3XXG4-P	V1.0 | Y | Q32BY200V10 | 2021-07-24 | Q3XXG406v10
| Q300G4 | Q3XXG4-P	V1.21/V1.1 | U | Q32BU200 | 2021-07-24 | Q3XXG405_11
| Q300G4 | Q3XXG4-P	V1.21/V1.1 | Y | Q32BY200 | 2021-07-24 | Q3XXG406v11
| Q300G4 | Q3XXG4-P	V1.2 | U | Q32EU200 | 2021-07-24 | 
| Q300G4 | Q3XXG4-P	V1.2 | Y | Q32EY200 | 2021-07-24 |