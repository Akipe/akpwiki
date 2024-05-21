---
title: Décorateur
description: 
published: true
date: 2024-05-21T17:48:37.546Z
tags: 
editor: markdown
dateCreated: 2024-05-21T16:04:49.014Z
---

# Décorateur

Permet d'ajouter dynamiquement des fonctionnalités supplémentaires à un objet.

Analogie avec pizzeria

patterne structurel

Ajoute des methodes dans des classes existantes, enveloppe des comportement à délégué à d'autres objets,

Comparaison poupé russe.

Exemple : réaliser ticket de caisse avec cout des ingrédient pour pizza à composé soit même.

Solution avec erreur :

1. pizza de base
1. Pizza tomate base & pizza creame base hérite de pizza de base
1. Ingrédients vous hérité de pizza de tomate, et il faudra refaire des ingrédients pour pizza creme

Attention ! restont POO

Principe ouvert / fermé : ouvert à la modif et fermé à la modification

IComponent : interface du composant : IElementPizza (description() & prix())
Concrete Component : composants concret : implémente IElementPizza PizzaBaseCreme & PizzaBaseTomate (element à décoré)
Base decorator (abstrait) : element decorator, implémente IElementPizza (IComponent)
Concrete Decorator : Ingrédient, comme Olive, Fromage, etc...

Code :


```c#

public class CreamBase : IElementPizza
{
	double Price
    double Description
    
    CreamBase()
    {
    	Price = 9;
        Description = "Pizza";
    }
}

public class Decorateur : IElementPizza
{
	IElementPizza elementToDecorate;
	double Price;
    double Description;
    
    CreamBase(IElementPizza elementToDecorate)
    {
    	Price = 1 + elementToDecorate.Price;
        Description = "Base creme" + elementToDecorate.Description;
    }
}


// Code client
IElementPizza myPizza = new CreameBase();
myPizza = new Anchoy(myPizza);
myPizza = new Chorizo(myPizza);
Console.WriteLine(myPizza.Description);
Console.WriteLine(myPizza.Price);
```

Avantage :
- etendre comportement objets sans heritage
- ajouter/retirer dynaniquement responsabilité objet
- (?) combiner plusieurs comportement en embalant plusieurs decorateurs
- Principe responsabilité unique respecté.

Inconvénient :
- ajoute une couche, qui peut complexifie les modifications

Commencé par les élément à décoré (Pizza base créme et base tomate), puis créer les élément qui vont "décorer" (ingrédient olibe, chorizo, fromage...).

---

- "La vie est belle" : on veut ajouter dans des balises html `<i>` et `<b>` : `<i><b>La vie est belle<\i><\b>`
  
- Objet à décorer : "La vie est belle".
- Décorateurs : `<i>` et `<b>`.

Decorateur peut décorer un texte ou un decorateur de texte, du coup il peut décorer un IElementDeTexte.

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-09/scaled-1680-/KdZYyeCyhQTVH1gQ-image-1662548028626.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-09/KdZYyeCyhQTVH1gQ-image-1662548028626.png)
  
```c#
// Gras
public string Afficher()
{
  return "<b>" + elementADecorer.Afficher() + "</b>;
}
```

Autre exemple :

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-09/scaled-1680-/iJXhY2m7CcdVq4xF-image-1663234994710.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-09/iJXhY2m7CcdVq4xF-image-1663234994710.png)

```c#
public float DeterminerPrix()
{
  return elementADecorer + Prix;
}
```

## Ressource

- <https://medium.com/@mazlum.tosun/pattern-decorator-revisit%C3%A9-en-java-8-3cd06789b767>
- <https://medium.com/@mazlum.tosun/pattern-decorator-revisit%C3%A9-en-java-8-3cd06789b767>