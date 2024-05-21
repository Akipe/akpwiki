---
title: Merise
description: 
published: true
date: 2024-05-21T15:34:38.728Z
tags: 
editor: markdown
dateCreated: 2024-05-21T15:34:38.728Z
---

# Merise

La méthode Merise est une méthodologie qui permet de correctement concevoir une application, que se soit son code source ou sa base de donnée, à partir de spécifications.

Elle se déroule en différentes étapes :
1. Dictionnaire de données
1. Régles de gestion
1. Dépendances fonctionnelles
1. MCD
1. MLD

## Les différentes phases de conception

### Le dictionnaire de données

| Entité | Mnémonique | Sens | Type | Taille | Remarques
|---|---|---|---|---|---
| livres | livre_isbn | Code ISBN unique du livre | AN | 13 | Identifiant
|  | id | Identifiant | N | 11 | Identifiant auto incrémenté
|   | livre_titre | Titre du livre | AN | 64 | Obligatoire
|   | date_achat | Date d'achat | D | YYYY-MM-DD | Non obligatoire
|   | enumeration_quelconque | Enumération | enum | 32 | Non obligatoire
|   | temps | Temps | T | hh:mm:ss | Non obligatoire


#### Longueur à définir en fonction des types

| Type | Nombre de chiffres | Range | 
|---|---|---
| byte | 3 | 0 à 255
| sbyte | 4 | -128 à 127
| short | 6 | -32 768 à 32 767
| ushort | 5 | 0 à 65 535 
| int | 11 | -2,147,483,648 to 2,147,483,647
| uint | 10 | 0 to 4,294,967,295
| long | 20 | -(2^63) to (2^63)-1
| ulong | 20 | 0 to 18,446,744,073,709,551,615
| float |  | 
| double |  | 
| decimal |  | 

### Les régles de gestion

Permet de définir les différentes relations ainsi que leurs cardinalités.

Exemple :

*One to one*

- **Un point de prêt** est localisé à **1 adresse**.
- **Une adresse** localise **0 ou 1 point de prêt**.

*One to many*

- **Un editeur** publie **1 ou plusieurs livres**.
- **Un livre** est publié par **0 ou 1 éditeur**.

*Many to many*

- **un client** emprunte **0 ou plusieurs exemplaires de livres**.
- **un exemplaire de livre** est emprunté par **0 ou plusieurs client**.

### Les dépendances fonctionnelles

[![04_functional_dependency_matrix.png](https://wiki.akipe.fr///uploads/images/gallery/2022-03/scaled-1680-/chdCHsnADAcy9IEE-04-functional-dependency-matrix.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-03/chdCHsnADAcy9IEE-04-functional-dependency-matrix.png)

### MCD

[![05_mcd.png](https://wiki.akipe.fr///uploads/images/gallery/2022-03/scaled-1680-/47YTol1FqBHs9Hiu-05-mcd.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-03/47YTol1FqBHs9Hiu-05-mcd.png)

### MLD

#### Visuelle

[![06_mld.png](https://wiki.akipe.fr///uploads/images/gallery/2022-03/scaled-1680-/yiiRirM7jsEhj4u3-06-mld.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-03/yiiRirM7jsEhj4u3-06-mld.png)

#### Textuelle

- Nom_table = (**<u>table_id</u>** INT, table_text VARCHAR(32), table_date DATE, #table_cle_etrangere)

### Les relations

| Relation | Nom de la relation | Concéquences
|---|---|---
| **0, 1** -> **1, 1** | **ONE to ONE** | Clé étrangère dans l'entité avec *(1, 1)*
| **1, N** -> **0, 1** | **MANY to ONE** | Clé étrangère dans l'entité faible *(0, 1)*
| **0, N** -> **0, N** | **MANY to MANY** | Relation intermédiaire avec pour clé primaire les clés étrangères des 2 entités
| **1, 1** -> **1, 1** | **ERREUR !** | Pas possible car erreur de conception, dans ce cas il faut fusionner les 2 tables

#### One to many

<div drawio-diagram="10" style="text-align:center;background-color:white;padding:20px"><img src="https://wiki.akipe.fr///uploads/images/drawio/2022-03/kRyTrtpFdlIjbl2V-drawing-5-1647250447.png"></div>

## Régles à respecter

### Formes normales

Ce sont des regles à respecter lors de la phase de conception.

Les régles suivantes impliquent que les précédentes ont été validés.


#### Forme normale 1 (FN1)

> Tous les attributs doivent être sémantiquement atomique

*(les attributs sont aussi petits que possible et ne peuvent pas être divisé en plus petits attributs)*.

#### Forme normale 2 (FN2)

> Doit respecter FN1 et tous les attributs d'une entité qui ne sont pas des identifiants doivent dépendre de l'identifiant en entier 

*(Ils ne doivent pas dépendre uniquement d'une partie de l'identifiant)*.

#### Forme normale 3 (FN3)

> Dois respecter FN2 et tous les attributs d'une entité qui ne sont pas des identifiants ne doivent dépendre que de l'identifiant de leur entité.
