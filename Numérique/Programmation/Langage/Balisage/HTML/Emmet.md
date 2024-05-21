---
title: Emmet
description: 
published: true
date: 2024-05-21T17:04:12.698Z
tags: 
editor: markdown
dateCreated: 2024-05-21T17:04:12.698Z
---

# Emmet

C'est une manière d'écrire plus rapidement du code HTML en utilisant des abréviations.

## Exemple

```
#page>div.logo+ul#navigation>li*5>a{Item $}
```

```html
<div id="page">
    <div class="logo"></div>
    <ul id="navigation">
        <li><a href="">Item 1</a></li>
        <li><a href="">Item 2</a></li>
        <li><a href="">Item 3</a></li>
        <li><a href="">Item 4</a></li>
        <li><a href="">Item 5</a></li>
    </ul>
</div>
```

## Résumé

| Ce qu'on veut écrire | Commande | Exemple
|---|---|---
| Un élément | `element` | `div`
| Un enfant | `elemnt>enfant` | `ul>li`
| Remonter | `element^parent` | `ul>li^p`
| Un élément à coté | `element1+element2` | `div+p+bq`
| Multiplicateur | `element*5` | `ul>li*5`
| Grouper | `(element)` | `(ul>li*2)+footer`
| Attribut id | `element#nomId` | `div#header`
| Attribut class | `element.nomClass` | `div.titreStyle`
| Mix attribut | `element.class#id` | `div#header.titre`
| Attributs personnalisés | `element[attribut="valeur"]` | `td[title="Hello world!" colspan=3`
| Incrémenter les nom d'attribut | `element.class$*5` | `ul>li.item$*5`
| Définir le texte | `element{texte}` | `a{Click me}`
| Lorem ipsum | `lorem` | `lorem100` (100 mots)

## Syntaxe

Documentation officiel : <https://docs.emmet.io/abbreviations/syntax/>

### Element

On peut utiliser n'importe quel nom des éléments HTML sans avoir à spécifier les chevrons.

Par exemple la commande :

```div``` :
```html
<div></div>
```

#### Raccourcie de nom

- `bq` : `blockquote`

### Enfants

Pour définir des balises enfants, on utilise `>`.

Exemple :

`div>ul>li` :
```html
<div>
    <ul>
        <li></li>
    </ul>
</div>
```

### Remonter

Lorsqu'on à défini des enfants et que l'on souhaite remonter, on utilise `^`. On peut en placer autant qu'on veut à la suite.

Exemple :

`div>ul>li^p` :
```html
<div>
    <ul>
        <li></li>
    </ul>
    <p></p>
</div>
```

### A coté

Pour définir des balises au même niveau, on utilise `+`.

Exemple : 

`div+p+bq` :
```html
<div></div>
<p></p>
<blockquote></blockquote>
```

### Multiplicateur

Pour multiplier un élément, on utilise `*`.

Exemple :

`ul>li*5` :
```html
<ul>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
</ul>

```

### Grouper

Si l'on veut groupes des abbrévations, on peut utiliser les parenthèses `(` et `)`.

Exemple :

`div>(header>ul>li*2>a)+footer>p` :
```html
<div>
    <header>
        <ul>
            <li><a href=""></a></li>
            <li><a href=""></a></li>
        </ul>
    </header>
    <footer>
        <p></p>
    </footer>
</div>
```

### Opérateurs d'attributs

#### id

On peut définir un id à un élément avec `element#nomId`.

Exemple :

`div#header` :
```html
<div id="header"></div>
```

#### classe

On peut définir une classe à un élément avec `element.nomClasse`.

Exemple :

`div.titreStyle` :
```html
<div class="titreStyle"></div>
```

#### Mix classe et id

On peut mixé les deux à la suite : `element#nomId.nomClasse`

#### Attribut pérsonalisé

On peut utiliser les crochets pour définir l'ensemble de tous les autres attributs : `element[nomAttribut="Une phrase" nomAutreAttribut=3]`

Exemple :

`td[title="Hello world!" colspan=3 autre]` :
```html
<td title="Hello world!" colspan="3" autre=""></td>
```

#### Incrémenter les valeurs des attribut

On peut également faire incrémenter les noms des attributs comme des classes ou des id par exemple, avec le symboe `$` qui correspond à un chiffre. On peut mettre autant de `$` que de chiffres qu'on souhaite.

Exemple :

`ul>li.item$*5` :
```html
<ul>
    <li class="item1"></li>
    <li class="item2"></li>
    <li class="item3"></li>
    <li class="item4"></li>
    <li class="item5"></li>
</ul>
```

`ul>li.item$$$*5`:
```html
<ul>
    <li class="item001"></li>
    <li class="item002"></li>
    <li class="item003"></li>
    <li class="item004"></li>
    <li class="item005"></li>
</ul>
```

On peut également définir une incrémentation ou de partir d'une valeur spécifique : [voir la documentation officiel](https://docs.emmet.io/abbreviations/syntax/#changing-numbering-base-and-direction)

### Ajout du texte

On peut utiliser les `element{}` pour définir le texte d'un élément.

Exemple :

`a{Click me}` :
```html
<a href="">Click me</a>
```

### Lorem ipsum

```lorem``` :
```
Lorem ipsum dolor sit amet, consectetur adipisicing elit. Qui dicta minus molestiae vel beatae natus eveniet ratione temporibus aperiam harum alias officiis assumenda officia quibusdam deleniti eos cupiditate dolore doloribus!
```

Par défaut, il génére 30 mots aléatoire repartient en plusieurs phrases.

Pour spécifier le nombre de mot : ```lorem100``` (pour 100 mots).
