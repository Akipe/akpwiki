---
title: Type MIME
description: 
published: true
date: 2024-03-04T13:05:41.359Z
tags: 
editor: markdown
dateCreated: 2024-03-04T13:05:41.359Z
---

# Type MIME


## Modèle mentale

C'est un standard qui permet de spécifier le type d'un fichier.

## Aperçu

Le Type MIME permet de définir le format d'un fichier à l'initialisation d'un transfert en réseau.

Il se définir textuellement comme ceci : 

```txt
type / sous type ; liste des paramètre (optionnel)
```

En plus des formats de type et de sous type standard, on peut facilement en ajouter de nouveaux.
## Profondeur

MIME est le sigle de Multipurpose Internet Mail Extensions. 

Il a été developpé initialement pour spécifier l'envoie de piéces jointes dans les émails.

On peut également le nommé *Media type*.

Plusieurs protocoles utilisent ce standard, notamment le [[Protocole HTTP]]. Pour ce protocole, le type MIME est envoyé lors de la [[Requête HTTP]]

chaque média est définir de la manière suivante :
```txt
type/sous type; liste des paramètre (optionnel)
```
Pour une image en format PNG :
```txt
image/png
```
Pour une page HTLM :
```txt
text/html; charset=utf-8
```

Il existe une dizaine de types :

- Application
- image
- text
- video

Pour définir des format personnalisées, il faut commencé par le caractère `x` :

```txt
image/x.icon
```

Pour les formats propriétaire, on commence par `vnd`  (vendor) :

```txt
application/vnd.ms-excel
```

On peut remplacer le `.` de la personnalisation par un `-`

Il permet d'éviter d'avoir besoin de regarder l'[[Extension de fichier]].

Des formats sont régulièrement ajouté dans le standard à la suite de [[RFC]]
## Schema


*Une image, un schéma ou un graphique de l'idée ou du concepts. Permet de comprendre en un coup d'œil.

## Quiz


```anki
deck: numérique
tags:
  - standard
  - données

---

Que signifie le cygle type __MIME__ ?

===

%Multipurpose Internet Mail Extensions%
```

```anki
deck: numérique
tags:
  - standard
  - données

---

Le __type MIME__ est définir de la sorte :

%type%/%sous type%; %liste des paramètre (optionnel)%
```

```anki
deck: numérique
tags:
  - standard
  - données

---

Par quoi commence les types personnalisées ?

===

%Par `x` suivi de `.` ou `-` comme `x.icon` ou `x-icon`%
```

```anki
deck: numérique
tags:
  - standard
  - données

---

Par quoi commence les types propriétaires ?

===

%Par `vnd` (pour vendor) suivi de `.` ou `-` comme `vnd.ms-office` ou `vnd-ms-office`%
```

```anki
deck: numérique
tags:
  - standard
  - données

---

Quel est le type MIME pour un fichier HTML encodé au format UTF-8 ?

===

%text/html; charset=utf-8%
```
