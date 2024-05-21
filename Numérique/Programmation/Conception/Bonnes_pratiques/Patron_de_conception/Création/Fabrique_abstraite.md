---
title: Fabrique abstraite
description: 
published: true
date: 2024-05-21T16:02:39.890Z
tags: 
editor: markdown
dateCreated: 2024-05-21T16:02:39.890Z
---

# Fabrique abstraite

Patterne de création

Permet de créer des objets à la chaine.

Fabrication à la chaine

Permet de définir pour différents objets des caractèristiques similaires :

- ordi bureau et serveur :
- fabrique "haut de game" et fabrique "bas de game"

Solution :

- pour utiliser des objets d'un même thème
- peremt de créer des objets à la chaine

Exemple : Ordinateurs

1. Fabrique concrètre (pc factory)
2. Classe contrète (pc)
3. classe abstraite : 

1. interface computerabstractfacotry
	method createComputer

2. serverfactory et pcfactory
	createComputer

3. classer computer :
	
Cass pc & classe serveur

Classe abstraite ComputerFactory.CreateCompuser(new PcFactory())

Classe abstraite ComputerFactory.CreateCompuser(new ServerFactory())

Positive :

- compatibilité
- découpler code client produit conceret
- principe responsaiblité unique
- principe ouvert / fermet

Exemple : fabrique de connexion de base de données : on donne les caractèristique de connexion à la bdd, la fabrique s'occupe de créer un objets représerntant notre bdd

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-09/scaled-1680-/HsPDHTr2OAOX4Cyx-image-1663235890047.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-09/HsPDHTr2OAOX4Cyx-image-1663235890047.png)
