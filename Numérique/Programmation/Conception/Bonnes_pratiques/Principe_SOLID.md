---
title: Principe SOLID
description: 
published: true
date: 2024-05-21T15:29:00.433Z
tags: 
editor: markdown
dateCreated: 2024-05-21T15:29:00.433Z
---

# Principe SOLID

SOLID est un acronyme qui definit les 5 principes à implémenter lors de la conception en programation orienté objet pour respecter les bonnes pratiques.

Voici la liste de ces principes :

- **S**ingle Responsibility Principle
- **O**pen/Closed Principle 
- *L*iskov Substitution Principle
- *I*nterface Segregation Principle
- *D*ependency Inversion Principle

## Les principes

### Principe de responsabilité unique

> Une classe doit avoir une seule et unique raison de changer, ce qui signifie qu’une classe ne doit appartenir qu’à une seule tâche.

Une classe n'a qu'un role. Si à la question "Qu'elle est le role de ma classe ?"

Une classe doit réaliser une seul chose.

Il faut découper une classes en plusieurs petits morceaux, chaque morceau ne faisant qu'une seul chose.

### Principe ouvert fermé

> Les objets ou entités devraient être ouverts à l’extension mais fermés à la modification.

Une fois que la classe est en production, on peut ajouter des fonctionnalités, mais pas la modifier.

- Ouvert : à l'extension (ajout de fonctionnalités)
- Fermé : à la modification (ne pas modifier le code déjà existant pour éviter les bugs)

### Principe de Substitution de Liskov

> Si q(x) est une propriété démontrable pour tout objet x de type T, alors q(y) est vraie pour tout objet y de type S tel que S est un sous-type de T.

Si on utilise le parent d'une classe, si on change les enfants, qu'on en ajouter, notre code doit pouvoir fonctionner.

### Principe de Ségrégation des interfaces

> Un client ne doit jamais être forcé à installer une interface qu’il n’utilise pas et les clients ne doivent pas être forcés à dépendre de méthodes qu’ils n’utilisent pas.

Il ne faut pas forcer le développeur à implémenter des fonctionnalités si ce n'est pas nécéssaire à ce que l'ont veut faire

### Principe d'inversion des dépendances

> Les entités doivent dépendre des abstractions, pas des implémentations. Il indique que le module de haut niveau ne doit pas dépendre du module de bas niveau, mais qu’ils doivent dépendre des abstractions.

Quand on veut des dépendances des classe, on fait la dépendances sur les interfaces et pas par des classes pour ne pas dépendre sur comment sont implémenté les classes.

## Ressources

- <https://www.digitalocean.com/community/conceptual_articles/s-o-l-i-d-the-first-five-principles-of-object-oriented-design-fr>
- <http://blog.ezoqc.com/5-exemples-faciles-pour-comprendre-les-principes-solid/>