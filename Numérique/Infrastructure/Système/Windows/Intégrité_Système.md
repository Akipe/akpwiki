---
title: Intégrité Système
description: 
published: true
date: 2024-04-21T14:51:57.740Z
tags: 
editor: markdown
dateCreated: 2024-04-21T14:51:57.740Z
---

# Intégrité Système

## Todo Windows Defender

### Réactualiser le cache des signatures de détection

*Clear cached detections and obtain the latest malware definitions.*

1. Open command prompt as administrator and change directory to `c:\Program Files\Windows Defender`
1. Run `MpCmdRun.exe -removedefinitions -dynamicsignatures`
1. Run `MpCmdRun.exe -SignatureUpdate`

Alternatively, the latest definition is available for download here: <https://docs.microsoft.com/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus>

## Étapes

1. Vérifier le disque et réparer les fichiers du disque.
1. Réparer avec `DISM`.
1. Réparer avec `sfc`.

## DISM

Ouvrir l'invite de commande en administrateur.

Vérifie si le système est endommagé :

```
Dism /Online /Cleanup-Image /ScanHealth
```

Vérifie si le système est réparable :

```
Dism /Online /Cleanup-Image /CheckHealth
```

Chemin du fichier de journalisation :

```
C:\WINDOWS\Logs\DISM\dism.log
```

### Système réparable

Réparer le système si celà est possible :

```bat
Dism /Online /Cleanup-Image /RestoreHealth
```

### Système non réparable (depuis système hote)

Il faudra utiliser l'image d'installation de Windows.

1. Récupérer le fichiers `source\install.wim` ou `source\install.esd` de l'image d'installation du système.
1. Lancer la récaparation.

Avec `install.wim` :

```
Dism /Online /Cleanup-Image /RestoreHealth /Source:wim:X:\sources\install.wim:N /LimitAccess
```

Avec `install.esd` :

```
Dism /Online /Cleanup-Image /RestoreHealth /Source:esd:X:\sources\install.esd:N /LimitAccess
```

Il faut remplacer `X` par la lettre du disque et `N` par l'index de l'édition de Windows à réparer.

### Réparer depuis l'environement de 

### Index

Correspondance des index :

| Index | Edition
|---|---
| 1 | Windows 10 Famille
| 2 | Windows 10 Famille N
| 4 | Windows 10 Éducation
| 6 | Windows 10 Professionnel

Afficher les index disponible dans le fichier install :

```
DISM /Get-WimInfo /WimFile:install.(wim|esd)
```

Obtenir des informations détaillé ususr un index :

```
DISM /Get-WimInfo /WimFile:install.(wim|esd) /Index:1
```

## SFC

```bat
sfc /scannow
```

Si la commande n'a pu réparer les fichiers, il faudra utiliser la commande `DISM`.

Chemin du fichier de journalisation :
```
%WinDir%\Logs\CBS\CBS.log
```

## Disque dur

```shell
chkdsk /f /r /x
```

## Ressources

- <https://winraid.level1techs.com/t/tip-for-win10-how-to-detect-and-repair-corrupted-system-files/31179>
