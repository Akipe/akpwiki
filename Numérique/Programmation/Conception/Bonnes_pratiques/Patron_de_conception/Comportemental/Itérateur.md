---
title: Itérateur
description: 
published: true
date: 2024-05-21T16:07:48.294Z
tags: 
editor: markdown
dateCreated: 2024-05-21T16:07:48.294Z
---

# Itérateur

Il permet de créer des iterateurs qui vont parcourir des collections. On peut personnalisé ces iterateur pour par exemple récupérer que des rectangles d'une collection de figures.

C'est pour iterer quelque chose dans des collections de types :

- lineaire
- carré
- arbre

Necessaire de les parcourir :

- du bas en haut,
- de haut en bas
- ou dans d'autre sens

Design patterne comportemental

Utilise lorsque le modèle a une structure complexe, comme une collection d'objet (plus complexe qu'un simple attribut).

Ce patron permet de protéger le code du développeur, et il protége l'ecriture de la collection et permet de reduire la taille du code.

- Avantage
	- responsabilité unique : on traite l'itération uniquement dans la classe
    - principe ouvert/fermé : on passe par une classe pour récupérer les élément de la calsse d'origine
    - on peut créer autant d'éterateur que l'on veut : en fonction de quoi on veut iterer, dans quel sens, etc...
- Désavantage
	- peut alourdir le code: pas nécessaire pour les collections simples.
    - peut être moins efficace que d'accéder directement aux objets
    
[![](https://wiki.akipe.fr///uploads/images/gallery/2022-09/scaled-1680-/cV16dAmjfbk5ltVV-image-1663244131726.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-09/cV16dAmjfbk5ltVV-image-1663244131726.png)