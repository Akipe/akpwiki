---
title: Composite
description: 
published: true
date: 2024-05-21T17:36:31.324Z
tags: 
editor: markdown
dateCreated: 2024-05-21T16:03:41.321Z
---

# Composite

Permet d'offrir un cadre de conception d'une conception d'une composition d'objets dont la profondeur de composition est variable, la conception étant basée sur un arbre.

Utile dans le cas d'arboréscences :

Une fenêtre A contient une fenêtre B qui contient une fenêtre C qui contient...

Celà représente un arbre binaire.

<https://upload.wikimedia.org/wikipedia/commons/d/d0/Arbre_binaire_ordonne.svg>

En winform, un `Control` est un **composant** car il contient d'autres éléments.

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-08/scaled-1680-/Jw5TfrT1Kpg0EHOE-image-1661947241627.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-08/Jw5TfrT1Kpg0EHOE-image-1661947241627.png)

On peut comparer cette représentation à un arbre inversé :
- le ***composant*** est le tronc de l'arbre : c'est les éléments les plus basiques *(ex: une forme géometrique)*
- ensuite les ***composite***, qui correspondent aux branches : c'est les éléments intermédiaires *(ex: un ensemble de figure géométrique)*
- enfin, on termine par ***les feuilles*** : c'est les éléments finaux, qui ne peuvent plus être décomposés *(ex: un triangle, rectangle, etc... mais aussi un personne créer à partir de ces figures)*

## Implémentations d'exemples

### Calculette

Dans un premier temps, il faut trouver une arborescence.

*1 + 2 + 3 : on a déjà 1 + 2 = 3, puis on a 3 + 3 = 6*

<div drawio-diagram="33"><img src="https://wiki.akipe.fr///uploads/images/drawio/2022-08/qWt4gy3vGqT7Lq1F-drawing-5-1659690987.png"></div>

`1 + 2 + 3` ->

`1`, `2` et `3` sont des nombres.

`1`, `2`, `3`, `1 + 2`, `x + 3` et `1 + 2 + 3` sont des expressions.

Une expression a besoin de deux expressions (c.a.d. dépendance binaire).

[![Calculette.png](https://wiki.akipe.fr///uploads/images/gallery/2022-08/scaled-1680-/4V5pFwQnB23OcPeC-calculette.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-08/4V5pFwQnB23OcPeC-calculette.png)

Résultat de l'exercice des expressions :

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-08/scaled-1680-/Oo2BO27amFbERDyJ-image-1661941830127.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-08/Oo2BO27amFbERDyJ-image-1661941830127.png)

- Evaluate : retourne le resultat de l'expression *(ex: 5)*
- Format : retourne le contenu de l'expression & le resultat *(ex: 3+2=5)*
- RepresentationOperation : retourne uniquement le contenu de l'expression *(ex: 3+2)*

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-08/scaled-1680-/gC80iSozK3DTHQkZ-image-1661942647448.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-08/gC80iSozK3DTHQkZ-image-1661942647448.png)

### Figures géometriques

Première version :

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-08/scaled-1680-/N3Ec9x3andMYfEur-image-1661950206572.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-08/N3Ec9x3andMYfEur-image-1661950206572.png)

Deuxième version, on utilisera le visiteur pour ne pas lier "SeDessiner()" à une interface graphique.

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-09/scaled-1680-/QecpcBb2TRHom8ek-image-1663235361059.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-09/QecpcBb2TRHom8ek-image-1663235361059.png)
