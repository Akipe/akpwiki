---
title: Programmation orienté objet
description: 
published: true
date: 2024-05-21T13:53:16.041Z
tags: 
editor: markdown
dateCreated: 2024-05-21T13:53:16.041Z
---

# Programmation orienté objet

La Programmation Orienté Objet (Ou POO) est un paradigme qui permet de simplifier le développement informatique en permettant de représenter des concepts en objets (comme dans notre quotidient) et de pouvoir les faire intérargir entre eux.

# Les types de représentations

## Classes abstraites

Une classe abstraite permet de créer un "modèle" utilisable pour des classes.

Tout comme les interfaces, elles mettent à disposition des methodes abstraites que les classes enfants devront implémenter.

**Une classe définissant une methode abstraite sera elle aussi obligatoirement abstraite**.

Un constructeur de classe abstraite pourra être utilisé par la classe enfant.

[![classe_abstraite_base.png](https://wiki.akipe.fr///uploads/images/gallery/2022-08/scaled-1680-/nIfKIKdpSZghAQLL-classe-abstraite-base.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-08/nIfKIKdpSZghAQLL-classe-abstraite-base.png)

## Interfaces

Les interfaces permettent de représenter des contrats que des classes peuvent implémenter.

On dit **qu'une classe réalise une interface** et non implémente.

[![interface_base.png](https://wiki.akipe.fr///uploads/images/gallery/2022-08/scaled-1680-/dui9RUrERP749Ivf-interface-base.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-08/dui9RUrERP749Ivf-interface-base.png)

On se moque de l'implémentation des methodes. Elle défini un contrat, les classe qui réaliseront l'interface devront implémenter les methodes.

On commence par identifier les fonctionnalités dont on aura besoin, qu'on définir dans des interfaces, pour au final les implémenter dans les classes.

On peut caster d'enfant à parent, mais il faut à tout prix éviter de caster un parent à un enfant.

```c#
// IBatiment.cs
public interface IBatiment
{
	// methode à implémenter dans les classes
	int SuperficieTotale();
}
```

```c#
// Batiment.cs
public class Batiment : IBatiment
{
	private int superficie;
    
    public Batiment(int superficie)
    {
    	this.superficie = superficie;
    }
    
    // On implémente la methode de l'interface
    public int SuperficieTotale()
    {
    	return 0;
    }
}
```

```c#
// Batiment.cs
public class MyClass
{
  public MyClass()
  { }
    
  public void AfficherBatiment(IBatiment batiment)
  {
    // _AfficherBatiment(batiment); <-- erreur, il faut éviter car cast de parent à enfant
  }
  
  private void _AfficherBatiment(Batiment b)
  {
    Console.WriteLine($"La superficie du batiment est ${b.SuperficieTotale()}");
  }
  
  private void _AfficherBatiment(BienImmobilier b)
  {
    Console.WriteLine($"La superficie du batiment est ${b.Loyer()}");
  }
}
```

```c#

```

```c#
// Program.cs
Batiment batiment = new Batiment(100);
MyClass myClas = new MyClass();
MyClass.AfficherBatiment(batiment);
```

Classe abtraite donne un début d'implémentation alors qu'une interface n'en donne aucune.

Une classe abtraite est utile lorsque du code est redondant.