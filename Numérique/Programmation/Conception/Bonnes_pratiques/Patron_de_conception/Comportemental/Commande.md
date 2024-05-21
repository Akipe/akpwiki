---
title: Commande
description: 
published: true
date: 2024-05-21T16:01:02.333Z
tags: 
editor: markdown
dateCreated: 2024-05-21T16:01:02.333Z
---

# Commande

Patron de conception comportemental.

Invocateur : réalise les commandes et gére l'historique

Receveur : La classe sur laquel les commandes vont agirs

ICommande : Interface qui va définir une convention de commandes

Commande1, Commande2, etc... : Commandes concrètes que l'ont va executer à travers l'invocateur.

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-09/scaled-1680-/NyG6we1j9TxcEDNI-image-1662535515685.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-09/NyG6we1j9TxcEDNI-image-1662535515685.png)

```c#
public void Realise(ICommande commande)
{
  commande.Executer();
}

public interface ICommande
{
  void Executer();
  void Annuler();
}
```

```c#
public class Invocateur
{
  public void Realise(ICommande commande)
  {
    commande.Executer();
  }
}
```

```c#
public class Invocateur
{
  public void Executer()
  {
    receveur.FaireAction();
  }
  public void Annuler()
  {
    receveur.FaireInverseAction();
  }
}
```

```c#
public class Receveur
{
  public void FaireAction()
  {
    // Code métier ...
  }
  public void FaireInverseAction()
  {
    // Code métier ...
  }
}
```