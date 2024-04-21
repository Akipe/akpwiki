---
title: Windows XP
description: 
published: true
date: 2024-04-21T15:18:14.693Z
tags: 
editor: markdown
dateCreated: 2024-04-21T15:18:14.693Z
---

# Windows XP

## Support USB

<https://lecrabeinfo.net/creer-une-cle-usb-dinstallation-de-windows-xp.html>
### WinSetupFromUSB

<http://www.winsetupfromusb.com/downloads/>

## Mise à jours

### Service Pack 3

Catalogue de mise à jour Microsoft Update : [Mise à jour KB936929](https://www.catalog.update.microsoft.com/ScopedViewInline.aspx?updateid=60b990a0-6efa-47be-8f5a-7df2c402583e)

- <https://assiste.com/Logitheque/Windows_XP_SP3.html>

### Service Pack 4

#### SP4 version assiste.com

<https://assiste.com/Logitheque/Windows_XP_SP4.html>

#### SP4 version harkaz

Windows XP SP4 Unofficial Final Version 3.1b & Post-SP4

- <http://www.ryanvm.net/forum/viewtopic.php?p=141144#141144>
- <https://drive.google.com/drive/folders/0B7k-l_4omFECNWRGNHBEdVBsTTA?resourcekey=0-_vid1f0NXhdIdIChxy8mkQ>

## Clés CD

###  Editions Universal Product Keys Collection

<https://github.com/fuwn/xp>

## Type de licences

### Changer

- <https://www.mydigitallife.net/how-to-change-windows-xp-version-between-retail-oem-and-volume-license-channel/>

#### PID

- Windows XP RTM
  - Retail: 51882335 (Retail edition accepting Retail CD keys)
  - Volume License: 51883270 (Volume License edition accepting Volume License keys or VLK)
  - OEM: 82503OEM (OEM edition accepting OEM keys or COA keys)
- Windows XP SP2
  - Retail: 55274335
  - Volume License: 55274270
  - OEM: 55277OEM
- Windows XP SP3
  - Retail: 76487335
  - Volume License: 76487270
  - OEM: 76487OEM

#### CD Volume label

- XP Home and Professional Combo = WXPHFPP_EN
- XP Home Retail = WXHFPP_EN
- XP Home Retail with SP1 = XRMHFPP_EN
- XP Home Retail with SP1a = X1AHFPP_EN
- XP Home Retail with SP2 = VRMHFPP_EN
- XP Home Upgrade = WXHCCP_EN
- XP Home Upgrade with SP1 = XRMHCCP_EN
- XP Home Upgrade with SP1a = X1AHCCP_EN
- XP Home Upgrade with SP2 = VRMHCCP_EN
- XP Home OEM = WXHOEM_EN
- XP Home OEM with SP1 = XRMHOEM_EN
- XP Home OEM with SP1a = X1AHOEM_EN
- XP Home OEM with SP2 = VRMHOEM_EN
- XP Home Volume = WXHVOL_EN
- XP Home Volume with SP1 = XRMHVOL_EN
- XP Home Volume with SP1a = X1AHVOL_EN
- XP Home Volume with SP2 = VRMHVOL_EN
- XP Professional Retail = WXPFPP_EN
- XP Professional Retail with SP1 = XRMPFPP_EN
- XP Professional Retail with SP1a = X1APFPP_EN
- XP Professional Retail with SP2 = VRMPFPP_EN
- XP Professional Upgrade = WXPCCP_EN
- XP Professional Upgrade with SP1 = XRMPCCP_EN
- XP Professional Upgrade with SP1a = X1APCCP_EN
- XP Professional Upgrade with SP2 = VRMPCCP_EN
- XP Professional OEM = WXPOEM_EN
- XP Professional OEM with SP1 = XRMPOEM_EN
- XP Professional OEM with SP1a = X1APOEM_EN
- XP Professional OEM with SP2 = VRMPOEM_EN
- XP Professional Volume = WXPVOL_EN
- XP Professional Volume with SP1 = XRMPVOL_EN
- XP Professional Volume with SP1a = X1APVOL_EN
- XP Professional Volume with SP2 = VRMPVOL_EN
- XP Professional Tablet PC with SP1 Disc1 = XRMPFPP_EN
- XP Professional Tablet PC with SP1a Disc1 = X1APFPP_EN
- XP Professional Tablet PC with SP2 Disc1 = VRMPFPP_EN
- XP Professional MSDN = WXPFPP_EN
- XP Professional MSDN with SP1 = XRMPFPP_EN
- XP Professional MSDN with SP1a = X1APFPP_EN
- XP Professional MSDN with SP2 = VRMPFPP_EN
- XP Professional Evaluation = WXPEVL_EN

## Maintenance

### Réparer les fichiers systèmes

Win + R puis `sfc /scannow`

## Configuration

### Optimisations

- <https://www.askvg.com/master-tutorial-to-make-your-windows-xp-super-fast/>

### Clés CD VL

```
MRX3F-47B9T-2487J-KWKMF-RPWBY
```
```
M6TF9-8XQ2M-YQK9F-7TBB2-XGG88
```

### Désactivation AutoRun (USB/CD)

#### Méthode 1

Regedit (fichier `DisableAutorun.reg`) :
```regedit
REGEDIT4
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\IniFileMapping\Autorun.inf]
@="@SYS:DoesNotExist"
```

#### Méthode 2

Install patch kb967715 Microsoft : <https://www.catalog.update.microsoft.com/Search.aspx?q=kb967715>

Ensuite dans les registres :

```
HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\Explorer\NoDriveTypeAutorun
NoDriveTypeAutoRun = 0xFF # désactiver tout type d'autorun
```

#### Méthode 3

Windows XP Pro :
> Démarrer > Exécuter > gpedit.msc > Modèles d'administration > Systèmes : Désactiver le lecteur automatique (une fenêtre s'ouvre, choisissez tous les lecteurs et cocher Activé

### Bootvis

- <https://www.majorgeeks.com/files/details/bootvis.html>

### Désactivation WGA (Windows Genuine Advantage)

```
- Step 1: First restart your PC into safe mode and log into the administrator account or any account with administrator privileges. You then must access both the Windows\system32 and Windows\system32\dllcache folders. Under these two folders are a file called WGATray.EXE. You must delete this file from both directories. This is what Windows Loads at start up to pop up the balloons when your copy of XP is loaded.

- Step 2: Now we have gotten rid of the executables, we need to remove the reference to the program for Windows to try and load. You will need to run the regedit program (Start -> Run -> then type “regedit”) from the run menu. Once in you need to navigate to:

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ Windows NT\CurrentVersion\WinlogonNotify

Once there you will see a folder called “WGALOGON”. This folder must be removed to prevent Windows XP even loading any of the DLL files associated with the WGA setup. Once you have managed this you can then restart you PC and no more of the annoying balloons, popups or timed login screens. This won’t get you around the access problems such as downloading files that aren’t for non genuine Windows versions, but there are no more annoying quirks to logging into your PC.
```

## Ajout fonctionnalités

### Support exFat

- <https://archive.org/details/winxp-exfat-driver>
- <https://archive.org/details/windows-xp-exfat-driver-kb955704-x86>

## Ressources

- <https://assiste.com/Windows_XP_Toutes_les_mises_a_jour.html>
- <https://forums.mydigitallife.net/forums/windows-xp-older-os.5/>
