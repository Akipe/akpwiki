---
title: Architecture applicative
description: 
published: true
date: 2024-05-21T16:21:05.035Z
tags: 
editor: markdown
dateCreated: 2024-05-21T16:21:05.035Z
---

# Architecture applicative

Il y a différentes manières de représenter un ensemble de classes partageant un théme ou un intéré :

- les paquets ou bibliothèques
- les couches

## Paquettage

Un paquet est un ensemble de classe, ayant un thème commun, relié dans un groupe de classe appelé bibliothèque (ou library en anglais).

On doit pouvoir si besoin utilisé un paquet d'un projet à un autre.

[![](https://wiki.akipe.fr/uploads/images/gallery/2022-10/scaled-1680-/teLhAHwTmPuc3rl6-image-1664960353614.png)](https://wiki.akipe.fr/uploads/images/gallery/2022-10/teLhAHwTmPuc3rl6-image-1664960353614.png)

[![](https://wiki.akipe.fr/uploads/images/gallery/2022-10/scaled-1680-/8vhgZ3VbggUBdRrn-image-1664960400386.png)](https://wiki.akipe.fr/uploads/images/gallery/2022-10/8vhgZ3VbggUBdRrn-image-1664960400386.png)

### Dépendance

Chaque paquet peut avoir une ou plusieurs dépendances.

Mais un paquet ne peut dépendre d'un autre paquet qui dépent lui même de ce paquet (pas de dépendances croisé).

<div drawio-diagram="103"><img src="https://wiki.akipe.fr/uploads/images/drawio/2022-10/eNixFUaTTwBOQGjY-drawing-5-1664960333.png"></div>

## Couches applicatives

Les couches applicatives (ou layers en anglais) sont un groupe de classes qui partages un but. On va faire une représentation "logique" de notre système.

Ces couches sont répartie en différents niveaux.

On peut comparer leur mode de fonctionnement avec le principe du modèle de couches OSI en réseau : chaque couche ne peut communiquer qu'avec les couches directement supérieur ou inférieur à elle.

Elles doivent pouvoir être indépendante, notamment pour :

- la gestion des extensions

Elle doivent également pouvoir être remplaçable par une couche du même niveau. Par exemple, on doit pouvoir remplacer une couche de persistance d'un base de données spécifique par une autre.

Il faut se poser la question du nombre de couches voulu pour notre système. Plus on défini de couches, plus on augmente le temps de développement. Moins on aura de couche, plus notre système sera "alourdi" par le nombre de classes par couche.

Les exceptions doivent être gérer par les couches, et sont remontés à la couche supérieur, qui pourra créer de nouvelle exceptions.

<div drawio-diagram="106"><img src="https://wiki.akipe.fr/uploads/images/drawio/2022-10/Qa0kydIbwFLnzAOF-drawing-5-1664962057.png"></div>

### Couches principales

Comme pour le modèle OSI en réseau, voici les différentes couches les plus utilisé, en partant de la couche la plus proche de l'utilisateur (IHM) et la couche la plus "profonde", qui s'occupe de la gestion du stockage de données :

1. couche présentation
1. couche coordination
1. couche service
1. couche domaine
1. couche persistance

Les couches 2 & 3 ont été ajouté plus tard dans l'histoire de l'informatique.

On doit pouvoir changer les différentes couches sans affecter les autres couches, c'est à dire bien séparer le code et les fonctionnalités de chaques couches et les rendres interchangeables (grace à des interfaces par exemple).

Il faut donc se poser la question de "Est-ce que la couche risque d'être changer?", pour la rendre interchangeable. Si non, ce n'est pas nécessaire.

Voici un exemple d'un système représenté en couche à travers un diagramme de paquettage :  
[![](https://wiki.akipe.fr/uploads/images/gallery/2022-10/scaled-1680-/5xy13OqmC7d2N9vm-image-1664978932275.png)](https://wiki.akipe.fr/uploads/images/gallery/2022-10/5xy13OqmC7d2N9vm-image-1664978932275.png)

#### Couche présentation

La couche **présentation** représente tout ce qui à attret à l'interface avec l'humain (IHM, client léger, lourd...). C'est cette couche qui change le plus souvent.

Il peut y avoir plusieurs couches parrallèle :

- client léger : web
- client lourd : desktop
- client riche : web + framework pour interractivité, comme un assemblage du léger et lourd.

#### Couche coordination

La couche **coordination** permet de séparer au maximum l'IHM de ce que l'on veut faire dans les couches inférieurs. C'est ici que l'on s'occupe de la gestion de la cinématique des écrans (grace aux controleurs par exemple).

#### Couche service

La couche **service** permet de proposer des actions clées en main et simple à utiliser.

Elle permet de cacher des complexités avec les classes métier de la couche domaine, et facilitant l'utilisation de plusieurs classes à travers une seul, ou de réaliser des vérifications qui seront similaires à l'ensemble des intérfaces classiques mais non nécéssaire pour les classes métiers.

> Par exemple dans le cadre d'un projet bancaire, on veut pouvoir gérer le des débit entre deux comptes. On ne veut pas savoir comment ça fonctionne : on cache donc la compléxité grace à un service, qui sera utilisable par nos couches supérieurs.

### Couche domaine

La couche **domaine** contiendra l'ensemble de nos classes métiers, c'est à dire de l'ensemble des classes liés fortement à la raison du projet du système.

C'est la seul couche que l'on ne veut pas changer, car elle contient tout le code métier du logiciel.

#### Couche persistance

La couche **persistance** est celle qui s'occupe de la gestion du stockage des données.

Elle peut être de toute sorte : sérialiser et la stocker dans des fichiers ou l'envoyer en réseau, s'occuper de sauvegarder les données dans une base de donnée, etc.  

### Couches supplémentaires

Il existe un certain nombre de couches que l'on peut rajouter à différents niveau.

#### Couche sécurité

La couche sécurité est celle qui fournit toute la securité pour l'ensemble des autres couches.

> Par exemple, le parfeu applicatif du framework Symfony, ou une couche de gestion du chiffrement.

#### Couche techniques

La couche techniques (ou Core Services) s'occupe de gérer l'ensemble du logiciel.

Elle peut comprend l'ensemble de ces fonctionnalités :

- La gestion des bugs
- renseigner et qualifier
- monitorer le système 
- gérer les logs

## Vue en niveau

On la nomme également en anglais "Tier View".

Vision plus physique sur la structuration de l'application. Chaque niveau est différencier par des composant différents qui communique grace à des protocoles d'échange.

On représente des couches séparé "physiquement" à notre système. Elles communiqueront grace à des protocoles d'échange, comme HTTP.

Par exemple, on représentera une couche liée à notre base de donnée et notre système, qui peuvent communiqué en réseau (par TCP/IP), ou bien une communication avec une autre application à travers son API (par HTTP).

Voici un exemple de vue en niveau en 2 tiers :  

<div drawio-diagram="109"><img src="https://wiki.akipe.fr/uploads/images/drawio/2022-10/IKqxs1GvuuvaWzwM-drawing-5-1664966049.png"></div>

Un autre exemple de vue en niveau en N tiers :  

[![](https://wiki.akipe.fr/uploads/images/gallery/2022-10/scaled-1680-/JTWcVQHUtLcvkegg-image-1664966672570.png)](https://wiki.akipe.fr/uploads/images/gallery/2022-10/JTWcVQHUtLcvkegg-image-1664966672570.png)

### Protocol de communication

- SOAP : ancetre API, permet de générer un sorte de "contrat" grace à de l'XML.
- HTTP / avec ou sans API REST
- GraphQL