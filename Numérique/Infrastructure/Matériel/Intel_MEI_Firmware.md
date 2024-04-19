---
title: Intel MEI Firmware
description: 
published: true
date: 2024-04-19T17:07:16.154Z
tags: 
editor: markdown
dateCreated: 2024-04-19T17:07:16.154Z
---

# Intel MEI Firmware

## Informations

Use the tool *Intel Converged Security and Management Engine Version Detection Tool (Intel CSME Version Detection Tool)* : <https://www.intel.com/content/www/us/en/download/19392/28632/intel-converged-security-and-management-engine-version-detection-tool-intel-csmevdt.html?v=t>

### MEAnalyzer

- <https://github.com/platomav/MEAnalyzer>

Installation :

- Installer Python (au minimum 3.7)
- `pip install colorama crccheck pltable`

Puis faire un dump du firmware actuel du systeme.

Puis lancer : `python MEA.py`

## Pilotes

- <https://winraid.level1techs.com/t/intel-converged-security-management-engine-drivers-firmware-and-tools-2-15/30719>

## Firmware

<https://winraid.level1techs.com/t/intel-converged-security-management-engine-drivers-firmware-and-tools-2-15/30719>

1. Analyser quel Intel MEI dispose le système, en utilisant HWInfo, MEAnalyzer & ...
   - Version (exemple : 8.1, build XXXX, hotfix XX)
   - Platform target market type : Consumer, Corporate...
   - Image type : 1.5MB ou 5MB
1. Télécharger les outils correspondant à la version majeur du système (`CSME System Tools` ou `ME System Tools`) : <https://mega.nz/folder/qdVAyDSB#FLCPaDVIsPYiy2TAUjD7RQ>
2. Faire un dump de la version actuel du firmware
   - Analyser avec MEAnalyser le firmware pour vérifier les infos
1. Vérifier les infos avec `MEInfo` :
   - `MEInfoWin64.exe` dans un terminal en admin
3. Télécharger le firmware correspondant à la version majeur : <https://mega.nz/folder/2Q0klQpA#6o04nlV_4xqfx76tjvgi4g>
4. Flasher
   - *Starting from CSME 12+, the main CSME firmware needs to be combined/stitched together with one or more IUPs first before initiating an update/downgrade procedure.*
     - `How to use FWUpdate Tool at CSME v13+:` : <https://winraid.level1techs.com/t/intel-converged-security-management-engine-drivers-firmware-and-tools-2-15/30719>
     - `How to use FWUpdate Tool at CSME v12:` : <https://winraid.level1techs.com/t/intel-converged-security-management-engine-drivers-firmware-and-tools-2-15/30719>
   - ((CS)ME >= 7) `FWUpdLcl -allowsv -f update_file_name.bin`
   - (ME <= 6) `FWUpdLcl update_file_name.bin -generic`

### Commandes

#### Sauvegarder le firmware actuel

Avec **FWUpdate** :

```powershell
FWUpdate\WIN64\FWUpdLcl64.exe -save CURRENT_FIRWARE_SAVED.bin
```

#### Mettre à jour le firmware

##### (CS)ME >= 7

```powershell
FWUpdate\WIN64\FWUpdLcl64.exe -allowsv -f UPDATE_FIRMWARE.bin
```

##### ME <= 6

```powershell
FWUpdate\WIN64\FWUpdLcl64.exe UPDATE_FIRMWARE.bin -generic
```

#### Information MEI systeme

```powershell
MEInfo\WIN64\MEInfoWin64.exe
```

#### Vérifier si MEI system fonctionnelle

```powershell
MEManuf\WIN64\MEManufWin64.exe -verbose
```

## Ressources

- <https://winraid.level1techs.com/t/intel-converged-security-management-engine-drivers-firmware-and-tools-2-15/30719>
- <https://www.tweaktownforum.com/forum/tech-support-from-vendors/gigabyte/54787-about-intel-management-engine-firmware>
- <https://winraid.level1techs.com/t/intel-converged-security-management-engine-drivers-firmware-and-tools-2-15/30719/1>
- <https://winraid.level1techs.com/t/intel-converged-security-management-engine-drivers-firmware-and-tools-16/89959>
- <https://winraid.level1techs.com/t/intel-converged-security-management-engine-drivers-firmware-and-tools-16/89959>
- <https://winraid.level1techs.com/t/guide-unlock-intel-flash-descriptor-read-write-access-permissions-for-spi-servicing/32449>
- <https://winraid.level1techs.com/t/guide-clean-dumped-intel-engine-cs-me-cs-txe-regions-with-data-initialization/31277>
- <https://winraid.level1techs.com/t/guide-disable-remove-intel-ibex-peak-me-6-0-ignition-firmware/31712>
- <https://winraid.level1techs.com/t/me-analyzer-intel-engine-firmware-analysis-tool-discussion/30876>
- <https://winraid.level1techs.com/t/intel-converged-security-trusted-execution-engine-drivers-firmware-and-tools/30730>