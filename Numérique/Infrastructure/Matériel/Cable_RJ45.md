---
title: Cable RJ45
description: 
published: true
date: 2024-04-19T17:19:39.414Z
tags: 
editor: markdown
dateCreated: 2024-04-19T17:19:39.414Z
---

# Cable RJ45

- <https://www.latelierducable.com/cable/cable-rj45/bien-choisir-son-cable-rj45/>
- <https://community.fs.com/fr/blog/t568a-vs-t568b-difference-between-straight-through-and-crossover-cable.html>

### Catégories (ou classe)

Ce sont les normes qui permettent de classer les cables RJ45 en fonction de leurs performances et la qualité des transmissions de données.

| Catégorie | Classe | Débit max | Fréquence | Blindage | Usage
|---|---|---|---|---|---
| CAT5 | D | 100 Mbit/s sur 100m | 100 Mhz | Non | Abandonné pour le CAT5e
CAT5e | De | 2,5 Gbit/s sur 100m et 10 Gbit/s sur 30m | 100 Mhz | Non | Réseau personnel de tous les jours
CAT6 | E | 5 Gbit/s sur 100m et 10 Gbit/s sur 55m | 250 Mhz | Oui / Non | Catégorie la plus courante
CAT6a | Ea | 10 Gbit/s sur 100m | 500 Mhz | Oui | Meilleure protection contre les interférences pour des débits rapides
CAT7 | F | 40 Gbit/s sur 50m et 100 Gbit/s sur 15m | 600 Mhz | Oui | Réseaux informatiques Ethernet qui nécessitent de très haut débits
CAT7a | Fa | 10 Gbit/s sur 100m et 40 Gbit/s sur 50m | 1 Ghz | Oui | Câbles entièrement blindés pour des applications industrielles et tertiaires
CAT8 | I / II | 25-40 Gbit/s sur 30m | 2 Ghz | Oui | Réservé aux datacenters

### Blindage

[![](https://wiki.akipe.fr///uploads/images/gallery/2023-05/scaled-1680-/Xg3Xvi9mC2qfumqU-image-1684690288712.jpg)](https://wiki.akipe.fr///uploads/images/gallery/2023-05/Xg3Xvi9mC2qfumqU-image-1684690288712.jpg)

[![](https://wiki.akipe.fr///uploads/images/gallery/2023-05/scaled-1680-/MtBoscIDmUEe7Ktk-image-1684692156980.jpg)](https://wiki.akipe.fr///uploads/images/gallery/2023-05/MtBoscIDmUEe7Ktk-image-1684692156980.jpg)

Exemple de choix de blindage pour utilisation cable appareil réseau :

| Catégotie | Blindage | Commentaires
|---|---|---
| CAT 5e | UTP | si la longueur est inférieur à 5 mètres et que l’environnement n’est pas perturbé
| CAT 5e | F/UTP | si la longueur est inférieur à 20 mètres et/ou que l’environnement peut être perturbé
| CAT 5e | SF/UTP | si l’environnement est fortement perturbé (assez rare dans un milieu domestique)
| CAT 6/6a | F/UTP | généralement utilisé dans le BTP pour son bon rapport qualité/prix
| CAT 6/6a | SF/UTP | si l’environnement risque d’être perturbé

#### U/UTP (UTP)

> *Unshielded / Unshielded Twisted Pair*

Niveau de blindage le plus bas, c'est à dire aucun blindage.

#### F/UTP (FTP)

> *Foiled / Unshielded Twisted Pair*

Les 4 paires de fils sont enveloppées ensemble par une feuillard en aluminium.

#### U/FTP (STP)

> *Unshielded / Foiled Twisted Pair*

Les 4 paires sont enveloppées une par une par un feuillard en aluminium.


#### S/FTP

> *Shielded / Foiled Twisted Pair*

Les 4 paires sont enveloppées une par une par un feuillard en aluminum, en plus d'être entouré d'une tresse de brins de cuivre.

#### F/FTP

> *Foiled / Foiled Twisted Pair*

Les 4 paires sont enveloppées une par une par un feuillard en aluminum, en plus d'être enveloppées ensemble par un autre feuillard en aluminium.

#### SF/UTP

> *Shielded Foiled / Unshielded Twisted Pair*

Les paires de fils sont torsadés, le tout est entouré d’un feuillard global et d’une tresse de brin de cuivre globale.

#### SF/FTP

> *Shielded Foiled / Foiled Twisted Pair*

Les paires de fils sont torsadés, les 4 paires sont enveloppées une par une par un feuillard, le tout est entouré d’un feuillard et d’une tresse de brins de cuivre globale.

### Monobrin et Multibrin

Celà caractèrise comment sont constitués les fils dans le cable.

#### Monobrin

[![](https://wiki.akipe.fr///uploads/images/gallery/2023-05/scaled-1680-/p0AiEFKMFGn7GrUl-image-1684692422904.jpg)](https://wiki.akipe.fr///uploads/images/gallery/2023-05/p0AiEFKMFGn7GrUl-image-1684692422904.jpg)

> Le file n'est faite que d'un seul brin épais de cuivre.

Utiliser pour un câblage permanent, notamment si encastré dans les murs. Il se monte normalement avec des connecteurs femelles à chaque extrémité, sauf cas particuliers.

#### Multibrin

[![mutlibrin.jpg](https://wiki.akipe.fr///uploads/images/gallery/2023-05/scaled-1680-/rkKCtIhgHAS4yHYx-mutlibrin.jpg)](https://wiki.akipe.fr///uploads/images/gallery/2023-05/rkKCtIhgHAS4yHYx-mutlibrin.jpg)

> Le file est faite de plusieurs brins fins de cuivre.

Destiné normalement à fabriquer des cordons de raccordement avec prises mâles.

### Droit et Croisé

Un connecteur est droit s'il respecte des deux cotés la même norme de couleur. Sinon, c'est un cable croisé.

#### Droit

Également appelé *cable de raccordement*.

Utilisé pour relier deux appareils n'ayant pas la même fonctionnalité réseau (1 ordinateur à 1 switch, etc).

[![](https://wiki.akipe.fr///uploads/images/gallery/2023-05/scaled-1680-/OS0GIHuI3f1kEgXe-image-1684691286085.png)](https://wiki.akipe.fr///uploads/images/gallery/2023-05/OS0GIHuI3f1kEgXe-image-1684691286085.png)

[![](https://wiki.akipe.fr///uploads/images/gallery/2023-05/scaled-1680-/khAv1N8ri6F87mqK-image-1684690758340.jpg)](https://wiki.akipe.fr///uploads/images/gallery/2023-05/khAv1N8ri6F87mqK-image-1684690758340.jpg)

#### Croisé

Utilisé pour relier des appareils réseaux "similaires", ayant la même fonctionnalité (2 switch, 2 ordinateurs...)

[![](https://wiki.akipe.fr///uploads/images/gallery/2023-05/scaled-1680-/zkPXidnlvqsFHxDQ-image-1684691258695.png)](https://wiki.akipe.fr///uploads/images/gallery/2023-05/zkPXidnlvqsFHxDQ-image-1684691258695.png)

[![](https://wiki.akipe.fr///uploads/images/gallery/2023-05/scaled-1680-/HJ5J1jaQzP4gyGA8-image-1684690773137.jpg)](https://wiki.akipe.fr///uploads/images/gallery/2023-05/HJ5J1jaQzP4gyGA8-image-1684690773137.jpg)

Par exemple pour connecter deux ordinateurs ensemble.

#### Cas d'utilisation

- Utiliser un câble droit pour le câblage suivant :
  - Switch vers le routeur
  - Switch vers PC ou serveur
  - Hub vers PC ou serveur
- Utiliser des câbles croisés pour le câblage suivant :
  - Switch vers switch
  - Switch vers hub
  - Hub vers hub
  - Routeur vers routeur
  - Port Ethernet du routeur vers PC NIC
  - PC vers PC

[![](https://wiki.akipe.fr///uploads/images/gallery/2023-05/scaled-1680-/5cXx3DTtvKiNX5QC-image-1684691062467.jpg)](https://wiki.akipe.fr///uploads/images/gallery/2023-05/5cXx3DTtvKiNX5QC-image-1684691062467.jpg)

### Norme de couleurs

[![](https://wiki.akipe.fr///uploads/images/gallery/2023-05/scaled-1680-/gq2n1TiNkCryGKvN-image-1684691149143.png)](https://wiki.akipe.fr///uploads/images/gallery/2023-05/gq2n1TiNkCryGKvN-image-1684691149143.png)

[![](https://wiki.akipe.fr///uploads/images/gallery/2023-05/scaled-1680-/EDpA7Uytf3j7fjZM-image-1684691108697.jpg)](https://wiki.akipe.fr///uploads/images/gallery/2023-05/EDpA7Uytf3j7fjZM-image-1684691108697.jpg)

**T568B** est généralement utilisée dans les installations commerciales, alors que **T568A** est plutôt répandue dans les installations résidentielles. 

**Pour un même cable, il est impératif que vous suiviez le même schéma de câblage que celui déjà entrepris.**

#### T-568B

C'est la norme la plus courante.

#### T-568A

T568A a été en grande partie remplacée par la norme T568B.

## Fabrication de cables

- <https://www.youtube.com/watch?v=HMIfUFeMfSk>

### Materiel nécessaire

#### Outils

- Pince à sertir RJ45
- testeur de cable RJ45/RJ11

#### Consommable

- cable rj75
- capuchon rj45
- embouts rj45 (prendre embouts avec possibilité de faire dépasser les 8 files pour une questions de praticité).

### Étapes

**Ne jamais tester ou réparer un cable RJ45 branché sur un appareil réseau !!!** Risque de court cirtcuits.

1. Inserer le capuchon du connecteur dans le cable avant toute opération.
2. Dénuder une bonne longueur du cable, en appuyant et faisant un petit tour avec la pince à sertir.
3. Retire les 2 couches de feuillares (blindage) et on mets de coté la prise terre.
4. Détorsade les 8 fils du cables.
5. Faire passer les 8 files dans l'embout.
6. Mettre en contacte la prise terre avec le connecteur metalique de l'embout.
7. Faire rentrer l'isolant du cable dans la prise et tout le reste.
8. Mettre le connecteur dans la pince à sertir.
9. Tout en tirant les 8 files pour mettre un pression de connecteur contre la prise, appuyer sur la prince pour sertir le cable.
10. Pousser le cable contre la prise pour mettre une pression contre la prise, et réappuyer plusieurs fois sur la pince confirmer que la prise est bien serti (8 fois)
11. Utiliser le testeur de cable pour vérifier que les files sont correctements connectés.


#### Si les fils ne sont pas tous valides

1. Avec la pince, remettre un coup de pression pour insister sur le sertissage.
2. Coupé un des bout du cable et recommencer.
3. S'il y a encors des problèmes, remplacer l'autre bout du cable.

## Achat

- <https://www.touslescables.com/>
- <https://www.comptoir-du-cable.com/>
