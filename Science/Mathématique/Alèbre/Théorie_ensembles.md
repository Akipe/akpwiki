---
title: Théorie des ensembles
description: 
published: true
date: 2024-09-08T15:08:55.498Z
tags: 
editor: markdown
dateCreated: 2024-09-08T11:52:49.812Z
---

# Théorie des ensembles

## Logique

*p* est une proposition.

### Négation

Négation : *non p* est **vrai** si *p* est **fausse** et **fausse** si *p* est **vrai**  

### Conjonction

Conjonction : *p et q* esy vrai si *p* et *q* sont vrai toutes les deux et fausse sinon  

### Disjonction

Disjonction : *p ou q* est vrai si l'une au moins est vrai, et fausse dans le cas où *p et q* sont fausses  

### Non contradiction

Non contradiction (contradiction) : *p et (non p)* est faux

### Principe tiers exclu

Principe du tiers exclu : *p ou (non p)* est vrai

### Double négation

Double négation : *p* et *non (non p)* sont équivalent

### Négation conjonction

Négation conjonction : *non (p et q)* et *(non p) ou (non q)* sont équivalent

### Négation de disjonction

Négation de disjonction : *non (p ou q)* et *(non p) et (non q)* sont équivalent

### Implication 

Si *p* implique *q*, celà veut dire que **si *p* est vrai, alors *q* l'est aussi**.

L'implication peut être fausse si la dernière affirmation n'est jamais ou pas toujours vrai.

Implication : p ⇒ q , *p implique q*, alors cet proposition est fausse uniquement si p est vrai et q faux. La relation ne se fait que dans un seul sens. p est *l'antécédent* et q son *conséquent*.

### Équivalence

Équivalence : p ⟺ q , *p si et seulement si q* ou *p et q sont équivalentes* est vrai si p et q ont la même valeur de vérité.


### Réciproque

Implication p ⇒ q, proposition q ⇒ p

### Contraposée

Implication p ⇒ q, proposition (non q) ⇒ (non p)

### Théorème négation de l'implication

non (p ⇒ q) = p et (non q)

Par négation :

p ⇒ q = (non p) ou q

### Théorème entre l'implication et  sa contraposée

p ⇒ q = (non q) ⇒ (non p)

### Théorème entre l'implication et son équivalence

p ⟺ q = (p ⇒ q) e (q ⇒ p)

### Quantificateurs

Exemple de prédicat à 2 arguments : =, ⩽, <

#### Quantifieur universel ∀

∀ x, P(x) === ∀ x ∈ E, P(x) - E est un ensemble - === ∀ x, (x ∈ E ⇒ P(x))

#### Quantifieur existentiel ∃

∃ x, P(x) === ∃ x ∈ E, P(x) - E est un ensemble - === ∃ x, (x ∈ E et P(x) - AU MOINS un élément de E a la propriété de P().

#### Négation ∀

non (∀ x ∈ E, P(x)) === ∃ x ∈ E, non P(x)

#### Négation de ∃

non (∃ x ∈ E, P(x)) === ∀ x ∈ E, non P(x) ∈ E

## Démonstration

### Inclusion ou égalité

Soit x ∈ E, montrons que x ∈ F : ...

Exemple :

> { x ∈ ℝ | ∃ y ⩾ 0, x ⩾ y } ⊂ ℝ+

Deux manière de montrer égalité :



### Double inclusion

Soit x dans E, montront que x est dans F. Puis pour y dans F, montront que y est dans E.

#### Par équivalence

Pour tout x : x ∈ E <=> ... <=> ... <=> x ∈ F