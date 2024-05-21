---
title: Sauvegarde
description: 
published: true
date: 2024-05-21T19:06:25.563Z
tags: 
editor: markdown
dateCreated: 2024-05-21T19:06:25.563Z
---

# Sauvegarde

[Sauvegarde : qu'est-ce que la règle 3-2-1 ?](<https://www.youtube.com/watch?v=xtks1mM0QfI>)

## Strategie de Sauvegarde

### Régle 3-2-1

> Toujours avoir **3 copies des données***

Cela inclut la copie originale et deux sauvegardes.

> Stocké sur **2 types de supports différents**

Par exemple, vous pouvez avoir une copie sur votre ordinateur et une autre sur un disque dur externe ou un service de cloud.

> Dont **1 copie hors site**

Il s’agit généralement d’une copie stockée dans le cloud ou dans un autre emplacement physique.

### Régle 3-2-1-1

Reprend la règle *3-2-1* mais avec :

> 1 copie des données **hors ligne**

Cette copie devrait être stockée de manière à ce qu’elle ne soit pas connectée à votre réseau, la protégeant ainsi des cyberattaques.

### Strategie multi-cloud

> Stockage des données sur plusieurs services cloud différents.

### Sauvegarde en continue

> Sauvegarder les données dès qu'elles sont disponibles et non à une interval fix


### Concepte Recovery Point Objective (RPO)

Correspond à la quantité de donnée que l'on peut se permettre de perdre. Par exemple un RPO de 4 heures veut dire que l'on peut perdre jusqu'à 4 heures de données.

### Concepte Disaster Recovery as a Service (DRaaS)

Service fourni par des tiers qui permet aux organisations de récupérer rapidement leurs données et de reprendre leurs activités après un incident.

## Materiel

### Disque Dur

#### Modèles et marques différentes

Il est important lors de la création d'une grappe de stockage de plusieurs disques dur. Celà permet d'éviter des pannes similaires, et en même temps.

### Sauvegarde sur supoort amovible

- <https://changelog.complete.org/archives/10500-recommendations-for-tools-for-backing-up-and-archiving-to-removable-media>
- <https://changelog.complete.org/archives/10516-using-git-annex-for-data-archiving>
- <https://changelog.complete.org/archives/10527-using-dar-for-data-archiving>
- <https://changelog.complete.org/archives/10535-backing-up-and-archiving-to-removable-media-dar-vs-git-annex>

## Outils

### Liste de logiciels

<https://www.complete.org/roundup-of-data-backup-and-archiving-tools/>

### Cloner une partition

#### Clonezilla

<https://clonezilla.org/clonezilla-live.php>

### Sauvegarde vers un service tiers

#### Rclone

Sauvegarder des données vers des services tiers comme des services clouds.

<https://rclone.org/>

## Service

### Stockage en ligne

Voir [Stockage en Ligne](https://wiki.akipe.fr///books/services-numerique/page/stockage-en-ligne)

## Ressources

- <https://blog.ostraca.fr/blog/regle-3-2-1-1-strategies-sauvegarde-cloud/>
- <https://www.reddit.com/r/DataHoarder/>