---
title: Pilotes Materiel
description: 
published: true
date: 2024-04-21T15:08:20.121Z
tags: 
editor: markdown
dateCreated: 2024-04-21T15:08:20.121Z
---

# Pilotes Materiel

Egalement appelé "drivers", se sont des logiciels qui permettent au système d'exploitation de communiquer avec le materiel.

## Inventaire materiel

- LibreHardwareMonitor <https://github.com/LibreHardwareMonitor/LibreHardwareMonitor>

## Site constructeur

| Nom | Type materiel | Adresse
|---|---|---
| [Nvidia](https://www.nvidia.fr/Download/Find.aspx?lang=fr) | Carte graphique
| [AMD](https://www.amd.com/en/support) | Carte graphique, Chipset et processeur
| [Intel](https://www.intel.com/content/www/us/en/download-center/home.html) | Processeur, chipset, carte graphique, carte réseau...
| [Realtek (réseau)](https://www.realtek.com/en/downloads) | Carte réseaux
| [Realtek (réseau 2)](https://www.realtek.com/en/component/zoo/advanced-search/72?Itemid=276) | Carte réseaux
| [Realtek (autre)](https://www.realtek.com/en/component/zoo/advanced-search/74?Itemid=276) | Carte audio, usb, peripheriques...
| [Microsoft](https://www.microsoft.com/en-us/download/driver.aspx) | Ordinateurs et périphérique
| [Google](https://developer.android.com/studio/run/win-usb) | Téléphone Android
| [Corsaire](https://www.corsair.com/us/en/downloads)
| [Asus](https://www.asus.com/support/download-center)
| [Asus ivanrf](https://ivanrf.com/en/latest-asus-drivers-for-windows-10/)
| [MSI](https://www.msi.com/support/download)
| [Asrock](https://www.asrock.com/support/index.fr.asp)
| [Asrock (derniers pilotes)](https://www.asrock.com/support/index.asp?cat=Drivers)
| [Asrock RackRack](https://www.asrockrack.com/general/products.asp)
| [Lenovo](https://support.lenovo.com/fr/fr)
| [Dell](https://www.dell.com/support/home/fr-fr?app=drivers)
| [Logitech](https://support.logi.com/hc/fr/articles/360024361233)

- <http://vogonsdrivers.com/index.php?catid=22>

## Site téléchargements pilotes

- <https://www.station-drivers.com/index.php/en-us/>
- <https://www.touslesdrivers.com/>
- <https://www.catalog.update.microsoft.com/Home.aspx>

### Asus

- <https://rog-forum.asus.com/t5/hardware-build-advice/index-all-my-drivers-firmware-software-threads/m-p/827232>
- <https://www.elevenforum.com/t/index-all-my-drivers-firmware-software-threads.11360/>

## Pilotes alternatifs

### Intel

#### AHCI (Intel Rapid Storage, RST & RSTi)

##### Pilote orininal Intel

- <https://winraid.level1techs.com/t/intel-rst-rste-drivers-latest-v19-5-5-1052-v8-0-4-1006/13801>

##### Pilote Moddifié

- <https://winraid.level1techs.com/t/modded-intel-ahci-and-raid-drivers-digitally-signed/19691>

1. Télécharger le pilote : <https://winraid.level1techs.com/t/modded-intel-ahci-and-raid-drivers-digitally-signed/19691>
1. Importer le certificat du développeur : <https://winraid.level1techs.com/t/tips-discussion-usage-of-mod-signed-drivers/31158#msg15574>
2. Installer le pilote

#### Intel (Converged Security) Management Engine (MEI)

- v16.0 : <https://winraid.level1techs.com/t/intel-converged-security-management-engine-drivers-firmware-and-tools-16/89959>
- autres : <https://winraid.level1techs.com/t/intel-converged-security-trusted-execution-engine-drivers-firmware-and-tools/30730>
- <https://station-drivers.com/index.php/en-us/component/remository/Drivers/Intel/Management-Engine-Interface-(MEI)/Drivers/16.x/lang,en-us/>

### Realtek UAD Driver

<https://github.com/pal1000/Realtek-UAD-generic>

4. Download latest Realtek UAD generic : <https://github.com/pal1000/Realtek-UAD-generic/releases>
5. Download latest DriverStore Explorer : <https://github.com/lostindark/DriverStoreExplorer/releases>
1. Disconnect from internet.
2. Uninstall current Realtek driver completely.
3. Reboot
6. Launch DriverStore Explorer and remove all Realtek Audio drivers
7. Launch terminal cmd as administrator
8. run `Realtek-UAD-generic\setup.cmd`
9. reboot

### AMD Aamernime

<https://www.amernimezone.com/>

## Trouver automatiquement dernier pilotes

### Constructeur

#### Intel

[Intel Driver & Support Assitant (Intel DSA)](https://www.intel.com/content/www/us/en/support/detect.html)

#### Nvidia

[NVIDIA GeForce Experience](https://www.nvidia.com/fr-fr/geforce/geforce-experience/)

#### AMD

[AMD Auto-Detect and Install Tool](https://www.amd.com/en/support/kb/faq/gpu-131)

### Indépendant

#### Mes Drivers

<https://www.touslesdrivers.com/index.php?v_page=29>

#### DriversCloud

<http://www.driverscloud.com/fr>

#### Snappy Driver Installer Origin

<https://www.glenn.delahoy.com/>

## Gestion

### Driver Store Explorer [RAPR]

Driver Store Explorer [RAPR] makes it easier to deal with Windows driver store. Supported operations include list/add/install/delete third-party driver packages.

<https://github.com/lostindark/DriverStoreExplorer>

### Display Driver Uninstaller (DDU)
<https://www.guru3d.com/files-details/display-driver-uninstaller-download.html>
