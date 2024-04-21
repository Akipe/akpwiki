---
title: Applications et Fonctionnalités
description: 
published: true
date: 2024-04-21T15:13:23.944Z
tags: 
editor: markdown
dateCreated: 2024-04-21T15:13:23.944Z
---

# Applications et Fonctionnalités

## Inventaire

### Materiel et logiciel

- <https://assiste.com/Liste_des_applications_installees.html>

#### msinfo

raccourcie : 

```batch
WINDOWS + R
```

Puis entrer :

```batch
msinfo32
```

#### LibreHardwareMonitor

<https://github.com/LibreHardwareMonitor/LibreHardwareMonitor>

#### HWiNFO

<https://www.hwinfo.com/download/>

#### WinAudit

<http://www.parmavex.co.uk/winaudit.html>

### License et clés CD

#### Licence Windows

##### Depuis le système

```batch
wmic path softwarelicensingservice get OA3xOriginalProductKey
```

```batch
powershell "(Get-WmiObject -query 'select * from SoftwareLicensingService').OA3xOriginalProductKey"
```

##### Depuis GNU Linux

```bash
sudo strings /sys/firmware/acpi/tables/MSDM | tail -1
```

#### Outils

##### ProduKey

<https://www.nirsoft.net/utils/product_cd_key_viewer.html>

##### SterJo Key Finder

<https://sterjosoft.com/key-finder.html>

##### PK Finder

<https://codedead.com/software/pk-finder>

##### Enchanted Keyfinder

<https://github.com/samrocketman/ekeyfinder>

##### recALL

<https://keit.co/p/recall/>

##### LicenseCrawler

<http://www.klinzmann.name/licensecrawler.htm>

## Desinstallation

### Outils

#### Bulk Crap Uninstaller

<https://www.bcuninstaller.com/>

## Tout en un

| Nom | Liens | Notes
|---|---|---
| optimizer | <https://github.com/hellzerg/optimizer> |
