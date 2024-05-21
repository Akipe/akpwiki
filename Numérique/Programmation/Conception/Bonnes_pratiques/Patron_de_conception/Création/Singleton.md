---
title: Singleton
description: 
published: true
date: 2024-05-21T17:38:57.022Z
tags: 
editor: markdown
dateCreated: 2024-05-21T15:57:01.679Z
---

# Singleton

## Utilité

Permet de s'assurer qu'une classe ne possède qu'une seule instance et de fournir une méthode unique retournant cette instance.

Il permet de résoudre le problème d'être sûr d'avoir une seul instance d'une classe.

*Par exemple, on a une classe qui gére la connexion à la base de donnée, on ne souhaite qu'une seul connexion.*

## Explication

[![Singleton.png](https://wiki.akipe.fr///uploads/images/gallery/2022-08/scaled-1680-/pXE2sYUcYIx27bCt-singleton.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-08/pXE2sYUcYIx27bCt-singleton.png)

Le constructeur de la classe Singleton devra être privé, car on ne souhaite controler sa création.

Du coup on utilise une méthode statique de cette classe qui va s'occuper d'instancier (ou pas si déjà instancier) une instance d'elle même.

Dans cette methodes, soit :

- on vérifie dans un attribut statique privé si il a déjà été instancié
- si oui on retourne cette instance
- si non on créer une instance, on l'enregistre dans l'attribut et on le renvoit

## Singleton

1. Constructeur privé.
2. Un attribut statique qui contiendra l'instance de la classe ou null, dans la classe elle-même.
3. Une methode "getInstance()" qui ;
	1. Est ce que l'instance existe ? si non elle le créer
    2. Renvoie l'instance

```c#
public class Loan
{
  private static Loan? instance = null;

  private Loan()
  {
  }

  public static Loan GetInstance()
  {
    if (instance == null)
    {
      instance = new Loan();
    }

    return instance;
  }
}
```
