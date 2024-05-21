---
title: CSS
description: 
published: true
date: 2024-05-21T14:24:52.497Z
tags: 
editor: markdown
dateCreated: 2024-05-21T14:24:52.497Z
---

# CSS


## Intégrer un fichier CSS dans un fichier HTML

```html
<html>
  <head>
    <link href="chemin/fichier.css" rel="stylesheet" type="text/css">
  </head>
</html>
```

## Selecteurs CSS

On peut selectionner les éléments HTML de plusieurs manières.  
Les selecteurs CSS n'ont pas tous le même niveau de priorité.

### Les tags (balises)

Il a le niveau de priorité le plus faible.

```css
p { /* On selectionne toutes les balises en les nommant (ici les balises <p>) */
  color: grey;
}
```

### Les classes

Il est prioritaire aux tags mais pas aux ids.

```css
.maClass { /* On selectionne les class en commançant par . */
  color: yellow; 
}
```

### Les id

Il a le niveau de priorité le plus élevé.

```css
#monId { /* On séléctionne les id en commençant par # */
  color: red;
}
```

### Les enfants de

On peut également selectionner les enfants d'un élément

### Liens

- Liste des selecteurs CSS : <https://www.w3schools.com/cssref/css_selectors.asp>
- s'entrainer aux selecteurs CSS : <https://flukeout.github.io/>

## Les variables

```css
:root{
  --main-bg-color: pink;
}

body {
  background-color: var(--main-bg-color);
}

```

## Couleurs

L'utilisation de la transparence permet à l'élément de mieux s'intégrés à la couleurs du fond.

Pour configurer des couleurs qui sont modifier par rapport à la couleur de l'élément ou du parent:

```css
.test {
  color: darker;
  background-color: currentColor;
}
```

### Unité de couleurs

- <https://www.swebdev.fr/blog/ameliore-ta-gestion-des-couleurs-avec-hsl>


### Thèmes sombres

- <https://lehollandaisvolant.net/?d=2023/06/17/14/36/05-astuces-css-pour-faire-un-theme-sombre>

## Bordures

Utilisation du box shadow plutot que border, pour des raisons de performances :  
<https://www.alsacreations.com/article/lire/1809-css-houdini-magie-ou-poudre-aux-yeux.html>

## Gérer les dimension

### En fonction de la taille de l'écran

- `px`: les pixels
- `in` : les pouces
- `cm` : les centimètres
- `mm` : les millimètres
- `pc` : les picas
- `pt` : les points
- `em` : elle est proportionnelle à la taille de la police de l’élément parent ou du document. Par défaut, 1 em = 16 px si aucune taille de police n’est définie.  
- `rem` : l’unité rem fait toujours référence à la taille de la police de l’élément racine. En d’autres termes, elle dépend du font-size définit par défaut.  
- `ex` : très rarement utilisée, cette unité est relative à la hauteur de la police actuelle en minuscule.  
- `ch` : cette unité est elle aussi peu utilisée, elle est relative à la largeur du caractère “0”.  
- `vh` : la hauteur du viewport (viewport correspond à l'ensemble de la page affiché par le navigateur)
- `vw` : la largeur du viewport
Les unités vh et vw sont similaires, à la seule différence qu’elles dépendent respectivement de la hauteur et de la largeur de la fenêtre de navigation.
- `vmin` : le viewport minimum
- `vmax` : le viewport maximum
- `%` : le pourcentage

Le pourcentage fait partie des unités relatives de façon générale puisqu’il s’adapte en fonction de son élément parent.

Ces deux unités de mesure en CSS fonctionnent selon le même principe.

## Responsive design

Minimum en pixel : 360px (ou 320 pour certains ancien mobiles)

## Gérer le positionnement

https://flexboxfroggy.com/#fr

### Flexbox

```css
.test {
  display: flex;
  flex-flow: row wrap;
  gap: 10px; /* Pour remplacer les margins */
}
```

Ressources en lignes :

- [CSS-Tricks: A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- apprendre à utiliser les flexbox : <https://flexboxfroggy.com/#fr>

### Grid

Ressources en ligne :

- [CSS-Tricks: A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
- apprendre à gérer les GRID : <https://cssgridgarden.com/#fr>

## Optimisation

### Détecter le code non utlisé

<https://purifycss.online/>