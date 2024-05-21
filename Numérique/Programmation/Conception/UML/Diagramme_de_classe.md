---
title: Diagramme de classe
description: 
published: true
date: 2024-05-21T15:37:57.456Z
tags: 
editor: markdown
dateCreated: 2024-05-21T15:37:57.456Z
---

# Diagramme de classe

Qualificateur : représente en UML des dictionnaire

Exemple : voiture et roue : utilisation d'un qualificateur (dictionnaire) avec :
- roue avant gauche
- roue avant droite
- roue arriere gauche
- roue arriere droite

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-09/scaled-1680-/2lEPLm8wbiirtxsm-image-1663059960468.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-09/2lEPLm8wbiirtxsm-image-1663059960468.png)


[![](https://wiki.akipe.fr///uploads/images/gallery/2022-09/scaled-1680-/uvXTr9Ar1KBMbMik-image-1662713409549.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-09/uvXTr9Ar1KBMbMik-image-1662713409549.png)

Une methode s'appelle **une operation**.

Termes :
- un objets est une instance de la classe.
- Une opération est une méthodes de classe.
- Un comportement est une méthodes d'un objet.
- encapsulation : caché la complexité à l'aide de methodes.
- Polymorphisme :
	- classe : Permet de pouvoir convertir un objet entre différentes classes grace à l'heritage, ce qui permet de lui faire changer son opération.
    - de methode : définir plusieurs methodes du même nom mais avec différent parametres.
    
## Les relations

A VERIFIER ET A MIEUX REDIGER

- Pour savoir si une association est une agrégation ou composition on se demande si on peut dire « est composé » si oui c’est l’un ou l’autre

Ensuite si le maximum est 1 (donc 0..1 ou 1) du côté du losange : c’est une composition (losange plein) si c’est 2 ou plus c’est une agrégation (losange vide)

- Moyen mnémotechnique pour le sens de la compo/agreg le losange « accroche » : une fête est composée d’invité → les invités « accrochent » la fête donc le losange est du côté fête.

- Une classe abstraite peut avoir un constructeur mais on ne peut pas l’instancier, seuls ses enfants peuvent l’utiliser

- Dépendance → le moins précis, si cela rentre dans rien, ils se connaisent et c’est une dépendance (par exemple il instancie une Voiture mais ne stocke pas d’attribut Voiture)


### Dépendance

### Association

### Agrégation

### Compositions

composition : comme corchet
si element composé d'autre chause :

composite 

Il faut se poser la question :

> Est ce que l'élément est composé de cette autre élément ?

**Moyen mémotechnique** pour le sens de la composition : A est composé de B, alors B s'accroche donc à A

```
B ---<> A
```

- Voiture & moteur
	- Une voiture est composé d'un moteur
	- Le moteur s'accroche donc à la voiture
    - moteur ---<> voiture

### Navigabilité

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-09/scaled-1680-/v9xniKOUWTmQ2i9L-image-1662706947255.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-09/v9xniKOUWTmQ2i9L-image-1662706947255.png)

Les fléchers lors des relations permettent de préciser que la classe connait la classe vers qui le flêche pointe (grace à un attribut).

### Classe d'association

Lorsqu'il y a, dans une association entre 2 classes, plus d'informations ou des actions qui sont lié à la réalisation de l'association, alors on devra créer une classe d'association.

Cette classe permet de relier les 2 classes.

Par exemple :

- Deux personnes peuvent se marrier : on ne relie pas une première personne à une autre, et ensuite l'autre, et il y aura différentes actions et informations défini lors du marriage, alors on devra créer une classe de "mariage" pour gérer tout celà.
- lors d'une inscription d'une personne à une formation, il faudra signer le contrat et réaliser différentes actions : on créera une classe d'association.

[![assoclass.gif](https://wiki.akipe.fr///uploads/images/gallery/2022-10/dd3Q9sImo5HTPsK3-assoclass.gif)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/dd3Q9sImo5HTPsK3-assoclass.gif)

## Les types de classes

### Interfaces

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-09/scaled-1680-/LqvVOjwk2NfB5GhS-image-1662712694347.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-09/LqvVOjwk2NfB5GhS-image-1662712694347.png)

## Stéréopytes

Les stéréotypes de classes permettent de définir leur rôles.

Il en existe un certain nombre :

- Classe "Boundary"
- classe entité
- classe de controle
- classe utilitaire
- Meta classe : classe pour définir les classes de base dans langages (gestion des int, et autres choses de bases)
- classe d'exception
- Interface
