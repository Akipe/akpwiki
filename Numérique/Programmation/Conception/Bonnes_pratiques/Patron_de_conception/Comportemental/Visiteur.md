---
title: Visiteur
description: 
published: true
date: 2024-05-21T15:59:21.275Z
tags: 
editor: markdown
dateCreated: 2024-05-21T15:55:52.996Z
---

# Visiteur

Permet de détacher des classes métier à différents contextes d'utilisation en séparant le code différents dans des classes externe.

Il permet de séparer un algorithme de la structure de l'objet.

Par exemple, on peut implémenter une logique de forme géométrique dans des entités, et définir les méthodes pour écrire ses formes dans des classes ***visiteur*** pour chaque interface graphique (console, winform et asp.net).

```c#
Rectangle r = new Rectangle(0, 1, 15, 20);
r.Accept(new VisiteurDeFigureConsole());
```

```c#
// Classe Rectangle
public void Accept(IVisiteurDeFigure visiteur)
{
  visiteur.Visit(this);
}

// Classe EnsembleFigure
public void Accept(IVisiteurDeFigure visiteur)
{
  visiteur.Visit(this);
  foreach( Figure f in figuresContenu)
  {
    f.Accept(visiteur);
  }
}
```

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-08/scaled-1680-/q4ufPKbObH6lNavE-image-1661951616310.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-08/q4ufPKbObH6lNavE-image-1661951616310.png)


---

(double dispatche)

On créer un classe intérmédiaire, qui va relier des classe entre elles en fonction de celles qui les appelles.

On va manipuler uniquement des interfaces, des deux cotés (visiteur et les visitable).

On envoie le visiteur (code métier).

1. Interface visiteur
2. Interface des visitable

```c#
public interface IVisitor
{
  public void VisiteBureau(Bureau batiment);
  public void VisiteCabinetMedical(CabinetMedical batiment);
  public void VisiteLocalCommercial(LocalCommercial batiment);
}
```

```c#
public interface IVisitable
{
  public void Accept(IVisitor visitor);
}
```

```c#
public abstract class BienImmobilier : IVisitable
{
  public abstract void Accept(IVisitor visitor);
}
```

```c#
public class Bureau : BienImmobilier // Implémente forcément IVisitable
{
  public void Accept(IVisitor visitor)
  {
    visitor.VisitBureau(this);
  }
}
```

```c#

```