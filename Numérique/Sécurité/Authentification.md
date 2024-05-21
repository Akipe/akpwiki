---
title: Authentification
description: 
published: true
date: 2024-05-21T12:36:05.825Z
tags: 
editor: markdown
dateCreated: 2024-05-21T12:36:05.825Z
---

# Authentification

## Mot de passe

### Bien choisir son mot de passe

- <https://aynils.ca/fr/information/choisir-un-mot-de-passe-securitaire/>

### Vérifier si compromisation

- <https://monitor.firefox.com/>
- <https://haveibeenpwned.com/>

### Dictionnaire

- base de donnée RockYou

### Attaque Brute Force

- <https://book.hacktricks.xyz/generic-methodologies-and-resources/brute-force>

### Hashage

Il existe différent algorithme de hashage :

- md5
- sha1
- sha256
- ...

#### Casser hashage

##### John the Ripper

Avec le logiciel **John the Ripper** : <https://github.com/openwall/john>

Casser des mots de passes de John the Ripper :

```bash
john FICHIER_CONTENANT_MOTDEPASSE.txt
```

Voir le résultat :

```bash
john FICHIER_CONTENANT_MOTDEPASSE.txt --show
```

```txt
NOM_UTILISATEUR:MOT_DE_PASSE
```

S'il ne connait pas le nom d'utilisateur, sa valeur vaudra `?`

##### Hashcat

<https://hashcat.net/hashcat/>

### Systèmes

#### GNU Linux

| Chemin | Type
|---|---
| `/etc/passwd` |
| `/etc/shadow`

#### Windows

##### Jayro's Lockpick

It is a bootable password removal suite, build with WinPE.

Official page is here : <https://gbatemp.net/threads/release-jayros-lockpick-a-bootable-password-removal-suite-winpe.579278/>

###### Download

Magnet link (v21.12) :

```txt
magnet:?xt=urn:btih:103B6A49FB23E2E9BDEAF7AF53E4BA533874574B
```

###### How to use

External tutorial : <https://community.lecrabeinfo.net/blogs/entry/332-supprimer-le-mot-de-passe-dun-compte-windows-avec-jayros-lockpick/>

### Astuces

- Lorsqu'il y a besoin d'une majuscule, c'est souvent le premier caractère qui l'est.
- Beaucoup de mot de passe font moins de 6 caractères.
- Une petite liste des mots de passes les plus utilisés :
	- `123456`
- Beaucoup de mots de passes sont basé sur (avec parfois un caractère special ou des chiffres à la fin) :
	- des prénoms
    - des marques de voiture
    - des clubs de sport
