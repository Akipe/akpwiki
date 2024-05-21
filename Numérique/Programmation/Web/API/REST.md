---
title: REST
description: 
published: true
date: 2024-05-21T16:24:13.381Z
tags: 
editor: markdown
dateCreated: 2024-05-21T16:23:44.901Z
---

# REST

> REST : **REpresentational State Transfer**

Une API REST (également appelée API RESTful) est une interface de programmation d'application (API) qui respecte une certaine contrainte de style d'architecture.

## Les 5 principes

### Separation of Concerns (Client & Server) / Modèle client-serveur

Une architecture client-serveur constituée de clients, de serveurs et de ressources, avec des requêtes gérées via HTTP. 

### Stateless / Sans état

Des communications client-serveur stateless, c'est-à-dire que les informations du client ne sont jamais stockées entre les requêtes GET, qui doivent être traitées séparément, de manière totalement indépendante

### Principe de système multicouche (layered)

Le principe de multicouche est de décomposer la gestion d'une API REST en différentes couches (ou strate), chaque couche ayant sa propre responsabilitée.

L'inverse du principe de multicouche serait de développer l'ensemble de notre API dans un unique fichier, en gérant à la fois la récupération de données, l'accès à la base de donnée et les logiques métier.

Même si les couches sont dissociées, elles interagissent entre elles et sont organisées de manière hiérarchisée. Ce découpage permet une meilleure séparation, ce qui aide à l'évolutivité et la modularité de notre application. On peut par exemple utiliser plus facilement différents langages pour chacune des couches.

<div drawio-diagram="14" style="text-align:center; padding: 20px;"><img src="https://wiki.akipe.fr///uploads/images/drawio/2022-03/2MdCgcoJTzOsB9Qg-drawing-5-1647859574.png" style="height: 350px"></div>

Un exemple de système multi-couche : le MVC pour Modèle Vue et Contrôleur

- Le modèle gère l'accès aux données à la base de donnée
- La vue permet de gérer l'affichage de la requête
- Le contrôleur va gérer les droits d'accès et orchestrer l'ensemble de la requête.

Vu que nos couches sont compartimentées, on peut mieux gérer le code legacy (ancien code à remplacer), en faisant tourner en parallèle une couche similaire plus récente.

On peut également "déplacer" nos différentes couches sur différents systèmes : découpler notre application sur plusieurs serveur et/ou sur différents sites, en interne à l'entreprise ou en externe, par exemple chez un hebergeur de Cloud.

Avec la gestion du réseau, on peut donc gérer l'accès aux différentes couches à l'aide de pare-feu et de proxy, pour améliorer la sécurité de l'application.

Voici quelques exemples de couches avec l'API REST :

- la couche DAO (Data Access Object)

Design pattern qui permet de faire le lien entre la couche métier et la couche de persistance. On s'abstrait de la façon dont les données sont stockées dans la couche métier.

- la couche DTO (Data Transfer Objects)

Design pattern qui permet de simplifier le transfère de données entre les couches. Il ne permet que de modifier ou d'accéder aux données.

- la couche modèle
- la couche contrôleur
- la couche service

#### Les différentes couches

##### Couche modèle

Elle permet de représenter les données qui peuvent être conservées dans la base de donnée : chacun des modèles représentable une table.

##### Couche DAO (Data Access Object)

La couche DAO est responsable de deux concepts, qui correspond à une seule entité :

1. Encapsuler les détails de la couche de persistance
2. Fournir une interface CRUD (Create, Read, Update, Delete)

##### Couche de services

C'est une couche qui est un peu plus haut niveau : elle est responsable du l'encapsulation de la logique métier, sans se limiter à celle-ci.

##### Couche de contrôleurs

Elle est responsable de prendre en charge le traitement des requêtes de la génération de la réponse à sa transissions. Elle appelle une ou plusieurs fonctions de la couche de service, et gère la sérialisation et la désérialisassent des données.

##### Couche DTO (Data Transfer Objects, objet de transfert de données)

La couche DTO est un objet qui transporte des données entre les processus. Ils sont utilisés pour découpler la représentation des données en objets de modèle.

### Uniforme / Interface uniforme

### Cacheable / Mise en cache

### Code on demand (optional) - Code à la demande

## Resources

- https://www.mulesoft.com/fr/resources/api/what-is-rest-api-design
- https://ichi.pro/fr/conception-d-une-architecture-multicouche-pour-la-creation-de-services-web-restful-avec-spring-boot-kotlin-177223107311561