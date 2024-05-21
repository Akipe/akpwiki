---
title: Visiteur
description: 
published: true
date: 2024-05-21T15:55:52.996Z
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