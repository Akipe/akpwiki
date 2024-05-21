---
title: Mocodo
description: 
published: true
date: 2024-05-21T18:34:32.815Z
tags: 
editor: markdown
dateCreated: 2024-05-21T18:34:32.815Z
---

# Mocodo

Mocodo permet de réaliser les différents diagrammes de la méthode Merise (MCD, MLD) : <https://github.com/laowantong/mocodo>

Documentation : <https://rawgit.com/laowantong/mocodo/master/doc/fr_refman.html>

## Exemple

### MCD

```
DF, 11 Élève, 1N Classe
Classe: Num. classe, Num. salle
Faire Cours, 1N Classe, 1N Prof: Vol. horaire
Catégorie: Code catégorie, Nom catégorie

Élève: Num. élève, Nom élève
Noter, 1N Élève, 0N Prof, 0N Matière, 1N Date: Note
Prof: Num. prof, Nom prof
Relever, 0N Catégorie, 11 Prof

Date: Date
Matière: Libellé matière
Enseigner, 11 Prof, 1N Matière
```

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-12/scaled-1680-/aF293sohyeGP35XD-image-1670762735948.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-12/aF293sohyeGP35XD-image-1670762735948.png)

### MLD

```
:::
Classe: Num. classe, Num. salle
:
Faire Cours: #Num. classe->Classe->Num. classe, _#Num. prof->Prof->Num. prof, Vol. horaire
:
Catégorie: Code catégorie, Nom catégorie
:


:
Élève: Num. élève, Nom élève, #Num. classe->Classe->Num. classe
:
Noter: #Num. élève->Élève->Num. élève, _#Num. prof->Prof->Num. prof, _Libellé matière, _Date, Note
:
Prof: Num. prof, Nom prof, #Code catégorie->Catégorie->Code catégorie, Libellé matière
:::
```

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-12/scaled-1680-/JvC5Rjzt4iYxtdmc-image-1670762763654.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-12/JvC5Rjzt4iYxtdmc-image-1670762763654.png)

## Compilateur

### Version en ligne

<https://www.mocodo.net/>
