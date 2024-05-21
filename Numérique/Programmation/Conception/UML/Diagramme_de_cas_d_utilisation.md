---
title: Diagramme de cas d'utilisation
description: 
published: true
date: 2024-05-21T15:52:28.343Z
tags: 
editor: markdown
dateCreated: 2024-05-21T15:52:28.343Z
---

# Diagramme de cas d'utilisation

Il est également appelé diagramme use case.

On défini les acteurs, qui sont des types d'utilisateur ou des logiciel externe (api, etc):

- Acteurs primaires (à gauche) : celui qui déclenche une fonctionallité du logiciel.
- Acteurs secondaires (à droite) : participe à un événement dont il n'est pas l'origine.

Un nom de cas d'utilisation commencer toujours par un verbe à l'infinitif. Il définit une macro fonctionnalité du logiciel.

Il faudra faire le moins de cas d'utilisation possible.

Il faut pas trop rentrer dans les détailles, et rester sur les fonctionnalités qui parle au client, en essayant de faire le moins possible.

Mais on peut définir des sous fonctionnalités redondantes.

## Représentation

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/FNTdRD1OtGBLVQm7-image-1665844371923.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/FNTdRD1OtGBLVQm7-image-1665844371923.png)

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/swO9R4TOehUaWgdw-image-1665844360271.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/swO9R4TOehUaWgdw-image-1665844360271.png)

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-09/scaled-1680-/cltc8d20h0KUQwLF-image-1663059329060.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-09/cltc8d20h0KUQwLF-image-1663059329060.png)

## Relations

### Bi-directionnel

Les trait simple permettent de transmettre l'information dans les deux sens.

### Uni-directionnel

Les fleches permettent de définir que l'information ne navigue que dans un seul.

#### Relation Include

Le terme `include` permet de définir l'obliger l'ajout d'une fonctionnalité :  
`A -- include --> B`: Quand A est fait, B l'est aussi.

#### Relations extends

Le terme `extend` permet de définir un lien optionnel.  
`A -- extends --> B`: Quand B est fait, A *peut* l'être.

Voici un moyen mémotechnique pour mémoriser la direction d'un extends :

> **Quand A extends B**, ça veut dire que **quand B est fait, A peut l'être**.

<div drawio-diagram="91"><img src="https://wiki.akipe.fr///uploads/images/drawio/2022-09/0SOl5xrB0nqfSHMg-drawing-5-1663665872.png"></div>

Quand on retire de l'argent, on peut éventuellement consulter notre compte.

<div drawio-diagram="92"><img src="https://wiki.akipe.fr///uploads/images/drawio/2022-09/wqpUkdhNX7rWh5w3-drawing-5-1663666098.png"></div>

#### Heritage

Possibilité d'héritage, mais à éviter !
