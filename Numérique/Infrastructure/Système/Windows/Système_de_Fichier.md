---
title: Système de Fichier
description: 
published: true
date: 2024-04-21T15:11:53.647Z
tags: 
editor: markdown
dateCreated: 2024-04-21T15:11:53.647Z
---

# Système de Fichier

## Lire

### Formats additionnel

<https://www.diskinternals.com/linux-reader/>

## Gérer

### DiskPart

Logiciel intégré à Windows en ligne de commande.

<https://lecrabeinfo.net/tutoriel-diskpart-creer-supprimer-manipuler-partitions-disque.html>

#### Effacer un disque

1. Lister les périphériques

```batch
list disk
```

2. Sélectionner le disque (remplacer X par le numéro de disque)

```batch
select disk X
```

3. Formatage rapide :

```batch
clean
```

3. (Bis) Formatage lent

```batch
clean all
```

4. Créer une nouvelle partition

```batch
create partition primary
select partition 1
```

5. Formater la partition dans un format de système de fichier

```batch
format fs=fat32 label="SAMSUNG" quick
```

```batch
format fs=ntfs label="KINGSTON" quick
```

6. (Bonus) Afficher format disponibles

```batch
list volume
select volume Z
filesystems
```

## Diagnostic

### Liste des partitions

#### ListParts

<https://www.bleepingcomputer.com/download/listparts/>

## Cache disque

<https://assiste.com/Cache_disque.html>

## Defragmentation

- <https://assiste.com/Defragmentation.html>
- <https://assiste.com/Defragmenter_le_registre_Windows.html>

## Réparation partition de données

### Check Disk (CHKDSK)

- <https://lecrabeinfo.net/chkdsk-verifier-et-reparer-les-erreurs-de-disque-sur-windows.html>
- <https://github.com/MicrosoftDocs/SupportArticles-docs/blob/main/support/windows-server/backup-and-storage/disk-space-problems-on-ntfs-volumes.md>
- <https://assiste.com/Commandes_Windows/chkdsk.html>
- <https://www.justgeek.fr/comment-verifier-et-reparer-un-disque-avec-chkdsk-sous-windows-11-88456/>

#### Terminal

##### Afficher l'aide

```batch
chkdsk /?
```

```txt
Vérifie un disque et affiche un rapport d’état.

CHKDSK [volume[[chemin]nom_de_fichier]]] [/F] [/V] [/R] [/X] [/I] [/C]
[/L[:taille]] [/B] [/scan] [/spotfix]

  volume              Spécifie la lettre de lecteur (suivie du signe
                      deux-points), le point de montage ou le nom de volume.
  nom_de_fichier      FAT/FAT32 seulement : spécifie les fichiers dont la
                      fragmentation est à vérifier.
  /F                  Corrige les erreurs sur le disque.
  /V                  Sur FAT/FAT32 : affiche le chemin d’accès et le nom complets de
                      tous les fichiers du disque.
                      Sur NTFS : affiche également les éventuels messages de                  nettoyage.
  /R                  Localise les secteurs défectueux et récupère les informations
                      lisibles. (implique /F lorsque /scan n’est pas spécifié).
  /L:taille           NTFS seulement : change la taille du fichier journal avec la
                      valeur spécifiée en kilo-octets. Si aucune taille n’est spécifiée, affiche la
                      taille actuelle.
  /X                  Force le démontage préalable du volume si nécessaire.
                      Tous les handles ouverts vers le volume ne sont alors plus valides
                      (implique /F).
  /I                  NTFS seulement : vérifie sommairement les entrées
                      d’index.
  /C                  NTFS seulement : ignore la vérification des cycles à l’intérieur de
                      l’arborescence de dossiers.
  /B                  NTFS seulement : réanalyse les clusters défaillants du volume
                      (implique /R).
  /scan               NTFS seulement : exécute une analyse en ligne sur le volume
  /forceofflinefix    NTFS seulement : (doit être utilisé avec « /scan »)
                      ignore toute la réparation en ligne ; toutes les anomalies trouvées
                      sont mises en file d’attente pour une réparation hors connexion (c’est-à-dire « chkdsk /spotfix »).
  /perf               NTFS seulement : (doit être utilisé avec « /scan »)
                      utilise davantage de ressources système pour effectuer une
                      analyse aussi rapidement que possible. Cela peut avoir un impact négatif sur les performances
                      d’autres tâches en cours d’exécution sur le système.
  /spotfix            NTFS seulement : exécute des corrections de points sur le volume.
  /sdcleanup          NTFS seulement : nettoie la mémoire des données de descripteur de sécurité inutiles
                      (implique /F).
  /offlinescanandfix  Exécute une analyse et une réparation hors connexion sur le volume.
  /freeorphanedchains FAT/FAT32/exFAT seulement : libère les chaînes de clusters orphelines
                      au lieu de récupérer leur contenu.
  /markclean          FAT/FAT32/exFAT seulement : marque le volume comme étant nettoyé si aucune
                      corruption n’a été détectée, même si l’option /F n’a pas été spécifiée.

Les options /I ou /C réduisent le temps d’exécution de Chkdsk en ignorant
certaines vérifications sur le volume.
```

##### Recherche rapide

```batch
chkdsk /f [lettre de lecteur:] 
```

##### Recherche approfondie

```batch
chkdsk /r [lettre de lecteur:]
```

##### Afficher un rapport d'état

```batch
chkdsk c:
```

### ntfsfix

Sous linux.

<https://github.com/tuxera/ntfs-3gg>
