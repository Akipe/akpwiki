---
title: Bios EFI
description: 
published: true
date: 2024-05-21T11:37:14.234Z
tags: 
editor: markdown
dateCreated: 2024-05-21T11:37:14.234Z
---

# Bios EFI

Website for learning :

- <https://www.bios-mods.com/>
- <https://www.bios-mods.com/forum/Forum-Tutorials>
- <https://www.bios-mods.com/forum/Thread-Tutorial-Thread-Index>
- <https://www.bios-mods.com/wiki/List_of_BIOS_Hacking_Websites>

## Lecture et flash

### Flash depuis puce bios

- <https://winraid.level1techs.com/t/guide-the-beginners-guide-to-using-a-ch341a-spi-programmer-flasher-with-pictures/33041>
- <https://winraid.level1techs.com/t/guide-using-ch341a-based-programmer-to-flash-spi-eeprom/30834>
- <https://winraid.level1techs.com/t/guide-flash-bios-with-ch341a-programmer/32948>

#### Matériel

- EZP2023

### Flash logiciel

- <https://winraid.level1techs.com/t/guide-how-to-flash-a-modded-ami-uefi-bios/30627>

#### Carte mère Gigabyte

Flash possible depuis le bios avec Q-Flash.

##### Erreur *Invalid BIOS Image*

- <https://winraid.level1techs.com/t/flashing-gigabyte-while-avoiding-invalid-bios-image/31185>

Utiliser :
- Efiflash DOS ou Efiflash UEFI : <https://winraid.level1techs.com/t/tool-efiflash-v0-80-v0-85-v0-87-for-gigabyte-motherboards/34071>

1. Create freedos usb key with Rufus
2. Put Efiflash mod to root usb key
3. Put bios file
4. Boot to usb key
5. Command "efiflash NAMEOFBIOS.FX"

#### Carte mère ASUS

##### Fichier BIOS *.ROM*

Aucune protection, possible utilisation de l'outil standart *EZ Flash*.

##### Fichier BIOS *.CAP*

Fichier protégés, impossible d'utiliser l'outil *EZ Flash*.

###### Avec ASUS *USB FlashBack*

<https://www.asus.com/support/FAQ/1038568/>

###### Avec *AMI AFUDOS* ou *AFUWIN*

1. Télécharger AMI AFUWin64 (ou AMI AFUDOS pour freedos) <https://onedrive.live.com/?authkey=%21AB4nZoUb2Q2nXMc&id=5014229B9E752333%21998&cid=5014229B9E752333>
2. Copier le bios d'origine non modifier dans le dossier de travail
3. Flasher le bios d'origine non modifier : `afuwinx64.exe ORIGINAL_BIOS.CAP`
4. Supprimer le *capsule header* depuis le bios modifié *.CAP* et sauvegarder ce bios modifié en format *.ROM*.
    - *The removal of the capsule header can be done by several BIOS tools. Here is the way how to do it by using the latest UEFITool version :*
        - Ouvrir avec UEFITool le bios *.CAP
        - Double cliquer sur *AMI Aptio capsule* qui devrait être à la racine du bios
        - Clique droit, choisir *Extract body...* et sauvegarder le fichier au format *.ROM*
1. Remplacer le fichier du bios original au format *.CAP* par le fichier de bios modifié au format *.ROM* dans le dossier de travail
2. Flasher avec la commade suivant : `afuwinx64.exe BIOS_MODDED.ROM /GAN`
3. Redémarrer

###### Avec *ASUS AI Suite*

1. Télécharger et installer AI-Suite
2. Démarrer *Easy Update for Bios Update* dans windows, selectionner le bios original non modifié.
3. Il y aura un certain temps d'attente de vérification par le logiciel AI-Suite
4. Une fois la vérification terminé et avant de lancer le processus de flash, remplacer le fichier de bios original non modifié par le fichier de bios modifié. Il faut qu'il ait le même nom et soit dans le même repertoire que le fichier original de bios.
5. Démarrer le processus de flash.

###### Avec flashrom

*Voir ci-dessous.*

#### Tous types de carte mère

##### Avec *Flashrom*

*recommended for 32MB sized BIOSes of AMD chipset mainboards*

*Fonctionne avec toutes les constructeurs de carte mère*

<https://flashrom.org/Flashrom>

1. Démarrer avec FreeDOS
2. Booter avec BIOS legacy avec CSM
3. Backup du bios actuel : `flashrom -p internal -r BACKUP.ROM`
4. Flash d'un nouveau bios : `flashrom -p internal -w NEW_BIOS.ROM`
    - *Users, who want to get a logfile about what exactly has been checked, detected and done by the tool, should execute the command with the suffix “ -o writelog.txt”*
1. Redémarrer

## Modifications

- Bios modding introduction & preparation : <https://winraid.level1techs.com/t/bios-modding-introduction-and-preparations/19335>
- Mod Your Own Bios / Discussions on BIOS Transcoding : <https://forums.mydigitallife.net/threads/mod-your-own-bios-discussions-on-bios-transcoding.378/>
- <https://forums.mydigitallife.net/threads/completely-new-to-bios-technology-read-here-first.819/>
- <https://forums.mydigitallife.net/threads/all-about-uefi-both-threads-are-merged-beta-testers-are-welcome.11157/>
- <https://fr.scribd.com/document/407446358/Practical-BIOS-Editing-pdf>
- `Practical_BIOS_Editing.pdf`

### Bios

#### Award Bios

- <https://www.bios-mods.com/forum/Thread-A-Learning-Guide-for-Using-Modbin6-for-Award-BIOS>

### EFI

#### Resizable Bar

- <https://winraid.level1techs.com/t/release-resizable-bar-dxe-driver/89534>
- <https://github.com/xCuri0/ReBarUEFI>
- common issues : <https://github.com/xCuri0/ReBarUEFI/wiki/Common-issues-(and-fixes)>
- <https://github.com/xCuri0/ReBarUEFI/wiki/Enabling-hidden-4G-decoding>
- <https://www.youtube.com/watch?v=vcJDWMpxpjE>

##### Check motherboard compatibility list

<https://github.com/xCuri0/ReBarUEFI/wiki>

#### Dell

- <https://github.com/vuquangtrong/Dell-PFS-BIOS-Assembler>

#### Aptio 4

#### Aptio 5

1. Ouvrir fichier bios avec MMTool, puis onglet "Option ROM".
2. Extraire le fichier OROM VBIOS en "vbios.dat".

#### Remove WLAN whitelist

- <https://medium.com/@p0358/removing-wlan-wwan-bios-whitelist-on-a-lenovo-laptop-to-use-a-custom-wi-fi-card-f6033a5a5e5a>
- <https://www.bios-mods.com/forum/Thread-General-method-to-remove-whitelist-from-Insyde-BIOS>

#### Modifier menu bios/efi AptioV

<https://winraid.level1techs.com/t/guide-usage-of-ami-s-aptiov-uefi-editor-fpt-flash-method/91842>

Tools available to modify menus :
- (AMI BIOS CONFIGURATION PROGRAM), some leaks on net (has bug with long string)
- BoringBoredom/UEFI-Editor, an open source web editor : <https://github.com/BoringBoredom/UEFI-Editor>

Tool used : BoringBoredom/UEFI-Editor

1. Use Intel FPT from CSME tools for flashing
  1. Check current system Intel MEI version, download tools corresponding :
      - <https://winraid.level1techs.com/t/intel-converged-security-management-engine-drivers-firmware-and-tools-2-15/30719>
      - <https://mega.nz/folder/qdVAyDSB#FLCPaDVIsPYiy2TAUjD7RQ>
  1. Bypass Intel AFT blocking (Work with BIOS LOCK & Flash Protection Range Registers (FPRR))
      1. Try if there is block :
          1. Run as admin terminal and go to `Flash Programming Tool\WIN32`
          2. Try to reflash current vendor bios with this command : `.\FPTW.exe -bios -rewrite -f .\BIOSFILE.ROM`
          3. IF there is an error (Error 368: failed to disable write protection for the bios space/ FPT Operation failed), you need to unblock, if there is no errors, pass to nexte steps
          4. Next, follow <https://winraid.level1techs.com/t/guide-usage-of-ami-s-aptiov-uefi-editor-fpt-flash-method/91842>
              - <https://github.com/datasone/setup_var.efi>
  2. Dump bios with Intel FPT (Flash Programming Tool) : `Flash Programming Tool\WIN32\FPTW.exe -bios -d bios_dump.bin`
  3. Editing dump bios dump :
  4. For flashing : `Flash Programming Tool\WIN32\FPTW.exe -bios -savemac -f bios_to_flash.rom` or if not working `Flash Programming Tool\WIN32\FPTW.exe -bios -f bios_to_flash.rom`
  5. Open this dump with UEFITool <https://github.com/LongSoft/UEFITool/releases>
  6. Search for `High Precision` or `HPET` (CTRL + F) (tab Text unicode)
      - will be `Setup` file DXE driver name and text
      - right click `PE32 image section` and `Extract as is...` : output a .sct file
  6. Search for `AMITSE` (CTRL + F) (tab Text unicode)
      - select with `LZMACUSTOMDECOMPRESSGuid`
      - right click `PE32 image section` and `Extract as is...` : output to `pe32`
  6. Search for `setupdata` (CTRL + F) (tab Text unicode)
      - select with `LZMACUSTOMDECOMPRESSGuid`
      - right click `setupdata` and `Extract body...`
  7. Generate IFR with UBU - AMI Setup IFR Extractor or <https://github.com/LongSoft/IFRExtractor-RS/releases>
  8. Go to <https://boringboredom.github.io/UEFI-Editor/> an put 4 files

#### NVME

- <https://winraid.level1techs.com/t/howto-get-full-nvme-support-for-all-systems-with-an-ami-uefi-bios/30901>

##### Tools needed

Choice between :
- AMI UEFI MMTool for your motherboard (v4 or v5)
- UEFITool <https://github.com/LongSoft/UEFITool/releases>
    - *Attention: The usage of the UEFITool is not recommended, if the opened BIOS contains one or more listed “Pad-Files” within or just beneath the “DXE Driver Volume”. A possible BIOS modding issue (removal of a natively present or addition of a natively not present “Pad File”) is caused by a wrong BIOS configuration and not by the UEFITool.*

EFI NVME bios modules :
- NvmExpressDxe_5.ffs (size 18kb), *best choice for system without native NVMe support
  - <https://mega.nz/file/FoInlQTR#tQrRIjjA7aNCdU9SduDfUaYfzsOhMQlJrwNKf6QRJ-o>
  - <https://1drv.ms/u/s!AjMjdZ6bIhRQhKMLdwiwyeVuUywa4A?e=GDoabL>
- NvmExpressDxe_Small.ffs (only 6 KB), *recommended for BIOSes with limited DXE Driver Volume space*
  - <https://mega.nz/file/IhBBQaIa#qBpnnX-cN9Fy5x1Usi5mOvV1tbqCe2px8amGtTw8_Aw>
  - <https://1drv.ms/u/s!AjMjdZ6bIhRQhKMM_vpOVkK8RHx-wA?e=ulwjvR>
  - The “Small” variant should be taken, if the BIOS tool gives you the message “File size exceeds the BIOS volume size” while trying to insert one of the above mentioned uncompressed modules.

After having successfully inserted any of the above offered NVMe modules the related name “NvmExpressDxe_5” resp. “NvmExpressDxe_Small” will be shown by the related BIOS tool.

##### Adding

1. Preparer le dossier de travail avec le bios "pure" à modifier (complétement extracté)
1. Créer un autre dossier qui contiendra le bios modifié
1. **Pour le bios ASUS avec extension *.CAP* :**
    - To avoid problems while trying to flash later on the modded *.CAP file via the ASUS USB Flashback method, it is recommended to extract the "Body" of the original *.CAP BIOS. This can easily be done with the UEFITool by opening the *.CAP file, doing a right-click onto the "AMI Aptio Capsule", choosing the "Extract body..." option and saving it as *.ROM file.
1. Dézipper les outils *(AMI Aptio MMTool, UEFITool)* et les modules NVMe dans le dossier de travail
1. Avec MMTool :
    1. Ouvrez le et charger le bios avec Load Image
    3. Parcourer la liste des élements dans le tableau en bas du logiciel (Volume, Index, FileName...) à la recherche d'un *FileName* nommé **CSMCORE**
    4. Cliquer sur la ligne contenant **CSMCORE**.
    5. Identifier la valeur **Vol. Index** vers la partie haute de l'application. Sa valeur correspond à la selection **CSMCORE**. Elle peut valeur *01*, *04*, *02:01.00* ou tout autre valeur...
    6. Since the CSMCORE module is present within nearly all AMI UEFI BIOSes and always located within the DXE Volume, where the NVMe module has to be inserted, you are now within the target Volume.
        - Note: In the very rare case, that the MMTool doesn’t show any module named “CSMCORE”, you should scroll down the MMTool window with the listed modules until you find the first ones with the letters “DXE” within its name. This way you can be sure, that you are within the correct “DXe Driver Volume”, where the NVMe module has to be inserted.
    1. VERIFIER BIEN que la valeur de **Vol. Index** correspond à celle du FileName **CSMCORE**.
    2. Appuyer sur l'onglet *Insert*, cliquez sur *Browser* pour selectionner le module NVMe au forma *pure* avec l'extension *.ffs*
    3. You can choose within the “Insert FFS Options” area of the MMTool GUI, whether you want to get the previously chosen module inserted “as it is” (normal option) or in “compressed” form (option in case of limited space within the DXE Volume).
       - Note: Don’t touch the “For Option ROM only” area of the MMTool GUI!
    1. Appuyé sur **Insert** pour intégrer le module
       - Note: If the MMTool should not be able to insert the desired module properly, the MMTool will give you a meaningful error message (e.g. “Not enough space within the Volume”). In this case you should try to get the “small” variant of the NVMe module in “compressed” form inserted. If there should not even be enough space for this small sized module, I recommend to post your specific BIOS modding problem into this thread and to attach the related original BIOS as *.ZIP or *.RAR archive file (if it should be bigger sized than 6 MB, post the download link). Then we will try to help you.
    1. Il faut à présent sauvegarder le BIOS modifié : appuyez sur le bouton **Save Image as..** à gauche du logiciel pour sauvegarder le bios
    2. Nous allons vérifier à présent : ouvrer le bios modifié avec MMTool
    3. Naviguer dans le tableau jusqu'à afficher CSMCORE, et naviguez jusqu'à la fin du volume qui le contient
       - Par exemple si CSMCORE est contenu dans le volume 03, allez jusqu'au dernier élément contenu dans ce volume, qui devrait être le module NvmExpressDxe
    5. Vous devriez vérifier le bios d'origine et le bios modifié avec  UEFITool, notamment pour vérifier si les **Pad-files** on été modifiés (invisible dans MMTool). Les seul différences entre les deux bios devraient être l'ajout d'un nouveau pilote DXE NvmExpressDxe*, tous les autres modules devraient être identique.

#### DSDT & SSDTs

- <https://github.com/lbschenkel/acer-sf314_43-acpi-patch>
- <https://forums.opensuse.org/t/how-to-fix-your-buggy-dsdt/774>
- <https://gist.github.com/raenye/d6645d7039a6136ccfb055e0f8517698>
- <https://gist.github.com/javanna/38d019a373085e1ba0c784597bc7ec73>
- <https://saveriomiroddi.github.io/Enabling-the-S3-sleep-suspend-on-the-Lenovo-Yoga-7-AMD-Gen-7-and-possibly-others/>
- <https://www.reddit.com/r/Dell/comments/kolf5f/patching_the_dsdt_table_to_enable_s3_suspend_on/>
- <https://www.tonymacx86.com/threads/guide-patching-laptop-dsdt-ssdts.152573/>
- <https://wiki.ubuntu.com/KernelTeam/HardwareEnableWithDSDT>
- <https://gist.github.com/mr-sour/e6e4f462dff2334aad84b6edd5181c09>
- <https://ubuntu.com/blog/debug-dsdt-ssdt-with-acpica-utilities>
- <https://forums.gentoo.org/viewtopic-t-122145.html>
- <https://unix.stackexchange.com/questions/371838/understanding-acpi-wake-up-codes-dsdt-differentiated-system-description-table>
- <https://dortania.github.io/Getting-Started-With-ACPI/Laptops/trackpad-methods/manual.html#checking-gpi0>
- <https://byronlathi.com/general/2022/02/26/16ach6-s3-state.html>
- <https://wiki.archlinux.org/title/DSDT>
- S3 sleep state
- <https://wiki.archlinux.org/title/Lenovo_IdeaPad_5_14are05#ACPI_patching>
- <https://www.reddit.com/r/AMDLaptops/comments/10ih90u/enable_s3_sleep_mode_on_lenovo_yoga_14_gen7_on/>
- <https://illumination2.wordpress.com/2019/09/12/dual-booting-mac-osx-and-windows-on-macbookpro/>
- <https://saveriomiroddi.github.io/Enabling-the-S3-sleep-suspend-on-the-Lenovo-Yoga-7-AMD-Gen-7-and-possibly-others/>
- <https://elitemacx86.com/threads/how-to-patch-laptop-dsdt-and-ssdts.178/>
- <https://github.com/CloverHackyColor/CloverBootloader/wiki/Fixing-DSDT>

- nice guide : <https://www.tonymacx86.com/threads/guide-patching-laptop-dsdt-ssdts.152573/>

##### ACPI

Getting started with ACPI : <https://github.com/dortania/Getting-Started-With-ACPI> & <https://dortania.github.io/Getting-Started-With-ACPI/>

- ACPI spec : <https://uefi.org/sites/default/files/resources/ACPI_Spec_6_4_Jan22.pdf>
- <https://github.com/jhand2/acpiparse>

#### GOP update & extraction tool (NVIDIA)

- <https://winraid.level1techs.com/t/gop-update-and-extraction-tool-nvidia-only/91381>

#### Legacy AMIBIOS8 settings

- <https://winraid.level1techs.com/t/guide-legacy-amibios8-make-all-compiled-settings-available/37221>
- <https://github.com/leveltrauma/obsolete_bios/blob/main/Obsolete_BIOS_Guide.pdf>
- <https://winraid.level1techs.com/uploads/short-url/1VaRHSE3ClT2kxZv8RE40YhoUBI.pdf>

```
41070E - UnitID Clumping
410C16 - GFX Card Workaround
411816 - MCU FW for erratum77
411914 - AddOn ROM Display Mode
412416 - Hide Unused PCIE P2P Bridges
412418 - OnChip SATA Channel
412710 - SET - Core Configuration GPP1 P0/1
412714 - Bootup Num-Lock
413018 - SATA IDE Combined Mode
413510 - SET - Core Configuration GPP2 P0/1
413514 - Wait For ‘F1’ If Error
414310 - Peer-to-Peer among GPP1/GPP2
414314 - Hit ‘DEL’ Message Display
414511 - HT Extended Address
41480E - PCIe = Maximum Payload Size
41491A - Load onboard SAS Option Rom
414D18 - Flash Controller
415311 - HT Link Tristate
415618 - SureBoot Feature
41591A - PS2 KB/MS Wakeup
41600E - PCIe = Maximum Read Request Size
416311 - IOC Peer-to-Peer Mode
417811 - SATA PHY WORKAROUND
417c18 - AMI OEMB table
417F1A - Retry Boot Devices
418111 - C States Support
418712 - USB Mass Storage Reset Delay
418D18 - Headless Mode
419214 - GART Error Reporting
41AC12 - Display Mode
41B411 - Relaxed Ordering
41B419 - Watch Dog function
41C219 - Raid CodeBase
41C411 - Extended Tag Field
41c518 - PEF SUPPORT
41D411 - No Snoop
41DD0D - NB Deempasies Level
41E411 - Extended Synch
41EF18 - MPS Revision
41F50D - HT3 Link Power State
41731A - Power Button Function
419C12 - Restore on AC Power Loss
415407 - Default Boot Order
41651A - Resume On RTC Alarm
414907 - RTC Alarm Date (Days)
418110 - NB-SB Link ASPM
413216 - NP NB-SB VC1 Traffic Support
41DF1A - SPD Software Write-Protect
41F40F - Power Down Enable
410410 - Power Down Mode
41991A - SMCCMOS Tool Support
41A71A - Auto Load Default from Optimal
410C15 - CS Sparing Enable
418119 - OnBoard Marvell NIC
418D19 - Marvell NIC OPTROM
41B20A - OnBoard PCI IDE Controller
413E18 - PATA Channel Config
41C417 - OHCI HC(Bus 0 Dev 18 Fn 0)
41D017 - OHCI HC(Bus 0 Dev 18 Fn 1)
41DF17 - EHCI HC(Bus 0 Dev 18 Fn 2)
41EE17 - OHCI HC(Bus 0 Dev 19 Fn 0)
41FA17 - OHCI HC(Bus 0 Dev 19 Fn 1)
410918 - EHCI HC(Bus 0 Dev 19 Fn 2)
411818 - OHCI HC(Bus 0 Dev 20 Fn 5)
413415 - Powerdown Unused lanes
414015 - Powerdown Unused lanes
414C15 - Powerdown Unused lanes
415815 - Powerdown Unused lanes
416415 - Turn Off PLL During L1/L23
417015 - Turn Off PLL During L1/L23
417C15 - Turn Off PLL During L1/L23
418815 - Turn Off PLL During L1/L23
414019 - USB 2.0 Controller Mode
415119 - BIOS EHCI Hand-Off
416219 - Legacy USB1.1 HC Support
419C19 - Northbridge interrupt pin
41190E - OnChip SATA Type
41240B - IDE Detect Time Out (Sec)
417712 - Legacy USB Support
413B09 - Remap Port Device Number
415F09 - Remap Port Device Number
418309 - Remap Port Device Number
41A709 - Remap Port Device Number
41CB09 - Remap Port Device Number
41EF09 - Remap Port Device Number
41130A - Remap Port Device Number
41370A - Remap Port Device Number
415B0A - Remap Port Device Number
417F0A - Remap Port Device Number
419110 - Gen2 High Speed Mode
41A310 - Gen2 High Speed Mode
41B510 - Gen2 High Speed Mode
41C710 - Gen2 High Speed Mode
41D910 - Gen2 High Speed Mode
41EB10 - Gen2 High Speed Mode
41FD10 - Gen2 High Speed Mode
410F11 - Gen2 High Speed Mode
412111 - Gen2 High Speed Mode
413311 - Gen2 High Speed Mode
413617 - Compliance Mode
414217 - Compliance Mode
414E17 - Compliance Mode
415A17 - Compliance Mode
416617 - Compliance Mode
417217 - Compliance Mode
417E17 - Compliance Mode
418A17 - Compliance Mode
419617 - Compliance Mode
41A217 - Compliance Mode
41AE17 - Compliance Mode
41C30C - Link Width
41D90C - Link Width
41EF0C - Link Width
415110 - Link Width
416110 - Link Width
417110 - Link Width
41D013 - Clear NVRAM
41510C - Core Configuration
41C70F - Reserved Memory Size
41EC13 - PCI IDE BusMaster
41690C - TX Drive Strength
417B0C - TX Drive Strength
418D0C - TX Drive Strength
419F0C - TX Drive Strength
41B10C - TX Drive Strength
419415 - TXCLK Clock Gating in L1
41A015 - TXCLK Clock Gating in L1
41AC15 - TXCLK Clock Gating in L1
41B815 - TXCLK Clock Gating in L1
41C415 - TXCLK Clock Gating in L1
41D015 - LCLK Clock Gating in L1
41DC15 - LCLK Clock Gating in L1
41E815 - LCLK Clock Gating in L1
41F415 - LCLK Clock Gating in L1
410016 - LCLK Clock Gating in L1
414C16 - Lane Reversal
415816 - Lane Reversal
416416 - Lane Reversal
417016 - Lane Reversal
417C16 - Lane Reversal
418816 - Lane Reversal
419416 - Lane Reversal
41FD18 - Active State Power Management
41AB11 - BMC Watch Dog Timer Action
41110C - Memory Timing Parameters
41340C - Memory Clock Speed
41AA18 - SR-IOV Supported
41B618 - ARI Forwarding
410814 - Quiet Boot
```

#### Intel FPT Error 280 / 368 bios lock Asus & other

- <https://winraid.level1techs.com/t/guide-grub-fix-intel-fpt-error-280-or-368-bios-lock-asus-other-mod-bios-flash/32725>

#### Enhanced Bios modding of Award Bioses

- <https://winraid.level1techs.com/t/guide-enhanced-bios-modding-of-award-bioses/30239>

#### Dumping EFI informations

- <https://github.com/SamuelTulach/efi-memory>
- <https://github.com/SamuelTulach/EfiDump>

#### AMI non-UEFI bios modding

- <https://winraid.level1techs.com/t/guide-ami-non-uefi-bios-modding/21509>

#### Recover flash from failed Bios flash with raspberry pi

- <https://winraid.level1techs.com/t/guide-recover-from-failed-bios-flash-using-raspberry-pi/30264>

#### AMI setup IFR Extractor AMISetupWriter

- <https://winraid.level1techs.com/t/tool-guide-ami-setup-ifr-extractor-amisetupwriter/32801>

#### Easy automated Mod tool for Coffee Lake bios

- <https://winraid.level1techs.com/t/tool-easy-automated-mod-tool-for-coffee-lake-bios/32795>

#### Award Phoenix BIOS modding

- <https://winraid.level1techs.com/t/guide-award-phoenix-bios-modding/25119>

#### H20EZE - Insyde "Easy BIOS Editor"

- <https://winraid.level1techs.com/t/tool-h20eze-insyde-easy-bios-editor/33332>

#### How to flash a modded AMI UEFI BIOS

- <https://winraid.level1techs.com/t/guide-how-to-flash-a-modded-ami-uefi-bios/30627>

#### Cofee Lake CPU on Skylake and Kaby Lake motherboards

- <https://winraid.level1techs.com/t/guide-coffee-lake-cpus-on-skylake-and-kaby-lake-motherboards/32344>

#### AMD CPU/chipset (todo)

- <https://www.overclock.net/threads/ryzen-bios-mods-how-to-update-bios-correctly.1640394/page-88>
- <https://www-hardwareluxx-de.translate.goog/community/threads/asus-prime-x370-pro-am4.1156996/?_x_tr_sl=auto&_x_tr_tl=en&_x_tr_hl=fr&_x_tr_pto=wapp#7.1>
- <https://forums-overclockers-ru.translate.goog/viewtopic.php?p=15090416&_x_tr_sl=auto&_x_tr_tl=en&_x_tr_hl=fr&_x_tr_pto=wapp#p15090416>
- <https://github.com/PSPReverse/PSPTool>

#### Enable Underclock

- <https://brendangreenley.com/undervolting-2020-dell-laptops-like-the-vostro-7500-and-more-tips-to-improve-thermals-battery-life-and-speed/#cpu-undervolt>

#### Flashing Gigabyte while avoiding “Invalid BIOS image” 

- <https://winraid.level1techs.com/t/flashing-gigabyte-while-avoiding-invalid-bios-image/31185>

#### AMD and Nvidia GOP update

- <https://winraid.level1techs.com/t/amd-and-nvidia-gop-update-no-requests-diy/30917>

#### Using Phoenix Tool for swapping Option ROM

- <https://winraid.level1techs.com/t/using-phoenix-tool-for-swapping-option-rom/30740>

#### Modifying/Flashing Dell Bios using PhoenixTool (Updating to new RST ROM) 

- <https://winraid.level1techs.com/t/guide-modifying-flashing-dell-bios-using-phoenixtool-updating-to-new-rst-rom/33181>

#### Manual AMI UEFI BIOS modding

- <https://winraid.level1techs.com/t/guide-manual-ami-uefi-bios-modding/22633>

#### Allow adjusting voltage

- <https://winraid.level1techs.com/t/request-gigabyte-aorus-15g-bios-unlocked/35453>

#### Transfer specific intel OROM VBIOS and GOP VBT settings using Intel BMP tool

- <https://winraid.level1techs.com/t/guide-transfer-of-specific-intel-orom-vbios-and-gop-vbt-settings-by-using-intel-bmp-tool/30930>

#### Recovery bios

- <https://forums.mydigitallife.net/threads/bios-recovery-procedures.870/>

#### How to Use New Phoenix Bios Mod Tool to Modify Phoenix/Dell/Insyde/EFI Bios Files

- <https://forums.mydigitallife.net/threads/how-to-use-new-phoenix-bios-mod-tool-to-modify-phoenix-dell-insyde-efi-bios-files.13358/>

#### Undocumented INSYDE BIOS recovery method

- Use andy's tool to obtain possible names.
- <https://forums.mydigitallife.net/threads/undocumented-insyde-bios-recovery-method-use-andys-tool-to-obtain-possible-names.13095/>

#### MSDM

- ( https://forums.mydigitallife.net/forums/mdl-projects-and-applications.34/page-2 )

#### OA 2.x SLIC & OEMCERT Collection

- <https://forums.mydigitallife.net/threads/oa-2-x-slic-oemcert-collection.5952/>
- <https://d-fault.nl/sliccerttest>
- <https://forums.mydigitallife.net/threads/oa-2-x-slic-oemcert-collection.5952/page-53#post-514521>
- <https://forums.mydigitallife.net/threads/intel-efi-bios-mod-for-slic-2-1.8249/>
- <https://forums.mydigitallife.net/threads/all-slics-2-x-modded-bios-list-note-for-requests-use-bios-mod-requests-section.7500/>
- <https://forums.mydigitallife.net/threads/how-to-permanently-add-slic-in-newer-asus-uefi.31404/>
- <https://forums.mydigitallife.net/threads/old-ami-bios-and-msdm-insertion.52378/>
- <https://forums.mydigitallife.net/threads/how-to-verify-the-digital-signature-of-a-slic-table.7532/>
- <https://forums.mydigitallife.net/threads/how-to-properly-identify-oem-certificates.4792/>
- <https://forums.mydigitallife.net/threads/tool-to-insert-replace-slic-in-phoenix-insyde-dell-efi-bioses.13194/>

##### SLP

- <https://forums.mydigitallife.net/threads/slp-marker-file-update-utilities.9055/>

#### Bios recovery procedure Dell

- <https://forums.mydigitallife.net/threads/dell-bios-recovery-procedure-confirmed.18959/>

#### HP BIOS MiniPCI Fix- nc6000/others

- <https://www.wimsbios.com/forum/topic9388.html>

#### Fix bios checksum

- <http://www.xtremesystems.org/forums/showthread.php?180607-Tutorial-How-to-fix-a-bios-checksum>

#### PH Insyde BIOS recovery steps

- <https://forums.mydigitallife.net/threads/hp-insyde-bios-recovery-steps.35272/>

#### AMI bios option ROM modding

- <https://forums.mydigitallife.net/threads/ami-bios-option-rom-modding-old-title-intel-ich9r-7-6-0-1011-rom.961/>

#### Dell BIOS Password

- <https://forums.mydigitallife.net/threads/faq-forgotten-dell-bios-password.43628/>

#### How to Modify Your Own Bios Using AMI Mod Tool and Award Mod Tool

- <https://forums.mydigitallife.net/threads/how-to-modify-your-own-bios-using-ami-mod-tool-and-award-mod-tool.6921/>

#### a way to mod insyde bios which can't be opened with ezh2o

- <https://forums.mydigitallife.net/threads/a-way-to-mod-insyde-bios-which-cant-be-opened-with-ezh2o.7470/>

#### How do I get the option in the bios to enable vt at Phoenix BIOSes???

- <https://forums.mydigitallife.net/threads/tutorial-how-do-i-get-the-option-in-the-bios-to-enable-vt-at-phoenix-bioses.35176/>

#### Secure Boot 'Golden' Key

- <https://forums.mydigitallife.net/threads/discussion-secure-boot-golden-key.70749/>
- <https://gist.github.com/acepace/df34b5213f1e0fae6529eb703d947187>
- <https://www.phoronix.com/news/Secure-Boot-Golden-Key>
- <https://www.theregister.com/2016/08/10/microsoft_secure_boot_ms16_100>

```
magnet:?xt=urn:btih:F2773357E95677E2B659CDFA1B4BE3631EE2897B&dn=SecureBoot.zip&tr=udp%3a%2f%2ftracker.openbittorrent.com%3a80%2fannounce&tr=udp%3a%2f%2ftracker.publicbt.com%3a80%2fannounce&tr=udp%3a%2f%2ftracker.ccc.de%3a80%2fannounce
```

## Outils

List of many apps : <https://www.tweaktownforum.com/forum/tech-support-from-vendors/gigabyte/30823-latest-overclocking-programs-system-info-benchmarking-stability-tools>

- <https://forums.mydigitallife.net/threads/bios-tools.529/>
- <https://onedrive.live.com/?authkey=%21AB4nZoUb2Q2nXMc&id=5014229B9E752333%21998&cid=5014229B9E752333>

### UEFITool

- <https://github.com/LongSoft/UEFITool>

### AMI Aptio V UEFI MMTool

- <https://softradar.com/fr/mmtool/>
- <https://mega.nz/#F!hZ8V0TKD!0OVo1pLEs2VmIYbRR0o7JQ>
- <https://vinafix.com/resources/mmtool.1144/updates>
- v4.50.0023 : <https://www.mediafire.com/file/1pgguc8q8lrornl/MMTool_Aptio_4.50.0023.7z/file>
- v5.0.0.7 : <http://downloads.hwbot.org/downloads/tools/X99/mmtool_v5.rar>
- v5.02.0024 mod : <http://www.mediafire.com/file/406suaf0vsb4x17/MMTool+5.02_patched.zip>

### AMI AFUDOS

- <https://www.bios-mods.com/forum/Thread-AMI-Bios-flash-tool-AFUDOS-EXE>

#### Commandes

- Display ROM file's ROM id

```shell
afudos BIOS_FILE.ROM /U
```

- Dump du bios actuel du système

```shell
afudos BIOS_FILE.ROM /O
```

- Mettre à jour uniquement le *Boot Block*

```shell
afudos BIOS_FILE.ROM /B
```

- Mettre à jour uniquement la *NVRAM*

```shell
afudos BIOS_FILE.ROM /N
```

- main BIOS image only

```shell
afudos BIOS_FILE.ROM /P
```

- Update Embedded Controller Block only

```shell
afudos BIOS_FILE.ROM /E
```

- Update Embedded Controller Block if newer version is detected

```shell
afudos BIOS_FILE.ROM /ECUF
```

- Update 2nd non-critical block only

```shell
afudos BIOS_FILE.ROM /K2
```

- Update main BIOS image, Boot Block and NVRAM at once

```shell
afudos BIOS_FILE.ROM /P /B /N
```

- Update whole BIOS ROM

```shell
afudos BIOS_FILE.ROM /P /B /N /C /E /K
```

- Update whole BIOS ROM and load current CMOS optimal settings

```shell
afudos BIOS_FILE.ROM /P /B /N /C /E /K /L0
```
```

- Update whole BIOS without checking ROM ID <-Don't use unless your sure

```shell
afudos BIOS_FILE.ROM /P /B /N /C /E /K /X
```
```

- Update whole BIOS with quiet execution

```shell
afudos BIOS_FILE.ROM /P /B /N /C /E /K /Q
```
```

- Update whole BIOS in quiet mode and REBOOT quietly

```shell
afudos BIOS_FILE.ROM /P /B /N /C /E /K /Q /REBOOT
```
```

- Update BootBlock MAC address<-Used for changing MAC if your mobo has onboard Ethenet that supports the option to boot from network

```shell
afudos BIOS_FILE.ROM /M "MAC_ADDRESS"
```
```

- Update whole BIOS and BootBlock MAC address<-Used for changing MAC if your mobo has onboard Ethenet that supports the option to boot from network

```shell
afudos BIOS_FILE.ROM /P /B /N /C /E /K /M "MAC_ADDRESS"
```
```

- Update whole BIOS but preserve SMBIOS type 0 and 11<-this prevents overwriting current DMI and CIM data at specific locations in the bios

```shell
afudos BIOS_FILE.ROM /P /B /N /C /E /K /R0 /R11
```
```

- 

```shell
afudos BIOS_FILE.ROM 
```
```

- 

```shell
afudos BIOS_FILE.ROM 
```

### Qflash

- <https://www.tweaktownforum.com/forum/tech-support-from-vendors/gigabyte/27805-bios-flashing-a-how-to-~-qflash-guide>

### UBU "UEFI Bios Updater"

- <https://winraid.level1techs.com/t/tool-guide-news-uefi-bios-updater-ubu/30357>
- <https://mega.nz/folder/k4Z0FAra#hMIhuLoTte8IcwtiDibiAw>
- <https://onedrive.live.com/?authkey=%21AB44B%2D0QUHMLW9g&id=5014229B9E752333%2166890&cid=5014229B9E752333>
- <<https://mega.nz/folder/lLg2GLrA#SnZZd0WjHkULFHg7FESm8g>

Téléchargement :
- <https://mega.nz/folder/k4Z0FAra#hMIhuLoTte8IcwtiDibiAw>
- <https://onedrive.live.com/?authkey=%21AB44B%2D0QUHMLW9g&id=5014229B9E752333%2166890&cid=5014229B9E752333>
- <https://mega.nz/folder/lLg2GLrA#SnZZd0WjHkULFHg7FESm8g>

Installation :
- Install Python (3.7 minimum)
- Install dependencies : `pip install colorama PLTable`
- Télécharger et placer "mmtool_a4.exe v5.0.0.7" : <http://downloads.hwbot.org/downloads/tools/X99/mmtool_v5.rar>
- Télécharger et placer "mmtool_a5.exe v5.02.0024 mod" : <http://www.mediafire.com/file/406suaf0vsb4x17/MMTool+5.02_patched.zip>
- Preparation Intel RST/RSTe rom/efi bios modules :
  - <https://winraid.level1techs.com/t/intel-efi-raiddriver-bios-modules/23689>
  - ahci & raid option rom : <https://winraid.level1techs.com/t/ahci-raid-option-rom-modules/17526>
- Préparation Intel iGPU VGA rom :
- Intel GopDriver : <https://winraid.level1techs.com/t/efi-lan-bios-intel-gopdriver-modules/33948>
- intel vbios and gop vbt settings : <https://winraid.level1techs.com/t/guide-transfer-of-specific-intel-orom-vbios-and-gop-vbt-settings-by-using-intel-bmp-tool/30930>
- other bios modules : <https://winraid.level1techs.com/t/updated-latest-rom-modules-not-ahci-raid-related/33911>
  - Realtek network : <https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software>
- microcode intel : <https://winraid.level1techs.com/t/offer-intel-cpu-microcode-archives/34261/165>
  - Download all microcode here : <https://github.com/platomav/CPUMicrocodes/tree/master/Intel>
  - Put theses files here : `Files\intel\mCode\SOCKET_VERSION`
  - Edit `Files\intel\mCode\MCUpdate.txt` and add line with new microcode path (exemple : `506E3 1151\cpu506E3_plat36_ver000000F0_2021-11-12_PRD_D39CBFD5.bin`)

### OROM_Replace

- <https://forums.overclockers.ru/viewtopic.php?f=25&t=479847>

### IFRExtractor RS

- <https://github.com/LongSoft/IFRExtractor-RS/>

### UEFIRomExtract

- <https://github.com/andyvand/UEFIRomExtract>

### AMIBCP

- 4.55.0070 : <https://www.mediafire.com/file/szfpa9kogiqhmw4/AMIBCP+4.55.0070.7z/file>
- 5.02.0031 : <https://www.mediafire.com/file/7shdrygf5tre1ve/AMIBCP+5.02.0031.7z/file>
- <https://www.reddit.com/r/overclocking/comments/cyj0c8/need_amibcp_v455v453_for_bios_modding_to_unlock/>

## Téléchargement

### Beta

- <https://www.tweaktownforum.com/forum/tech-support-from-vendors/gigabyte/28656-gigabyte-latest-beta-bios>

### Modded

- <https://www.tweaktownforum.com/forum/tech-support-from-vendors/gigabyte/48290-gigabyte-modified-bios>
- <https://winraid.level1techs.com/c/bios-uefi-modding/offers-already-modded-special-bioses/28/none>

## Ressources

- <https://winraid.level1techs.com/t/bios-modding-introduction-and-preparations/19335>
- <https://hardforum.com/threads/tools-to-flash-and-recover-bios-on-asus-p8xxx-boards-fd44editor-ftk.1726429/>
- <https://winraid.level1techs.com/t/guide-manual-ami-uefi-bios-modding/22633>
- <https://winraid.level1techs.com/t/guide-how-to-flash-a-modded-ami-uefi-bios/30627>
- <https://firmwaresecurity.com/>
- <https://winraid.level1techs.com/t/guide-how-to-extract-insert-replace-efi-bios-modules-by-using-the-uefitool/32122>
- <https://winraid.level1techs.com/t/flashing-bios-chip-mx25l3205d-with-ch341a-progammer-cant-detect-chip/32690/10>
- <https://winraid.level1techs.com/t/guide-recover-from-failed-bios-flash-using-raspberry-pi/30264#msg76839>
- <https://winraid.level1techs.com/t/guide-nvme-boot-without-modding-your-uefi-bios-clover-efi-bootloader-method/31665>
- <https://winraid.level1techs.com/t/guide-nvme-boot-for-systems-with-legacy-bios-and-uefi-board-duet-refind/32251>
- <https://github.com/platomav/CPUMicrocodes>
- <https://winraid.level1techs.com/t/help-needed-asrock-x99-taichi-modding-rebar-cpu-microcodes-default-bios-values/91869>
- <https://winraid.level1techs.com/c/bios-uefi-modding/bios-modules-pci-rom-efi-and-others/13/none>
- <https://winraid.level1techs.com/t/bios-modding-success-failure-overview/30247>
- <https://winraid.level1techs.com/t/request-how-to-access-locked-hidden-bios-menu-settings/32688/4>
- <https://winraid.level1techs.com/t/solved-how-do-i-get-hidden-menus-shown-within-ifs-form-sets/33154#msg73071>
- <https://winraid.level1techs.com/t/overpowered-tongfang-cyberpower-machrevo-machenike-unlocked-bios-guide-w-files/33133>
- <https://forums.mydigitallife.net/forums/bios-mods.25/>
- <https://forums.mydigitallife.net/threads/this-is-no-request-thread-hp-compaq-bioses-how-to-modify-the-bios.7681/>
- <https://4pda.to/forum/index.php?showtopic=421276>
