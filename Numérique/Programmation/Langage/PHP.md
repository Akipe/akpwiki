---
title: PHP
description: 
published: true
date: 2024-05-21T14:07:02.223Z
tags: 
editor: markdown
dateCreated: 2024-05-21T14:07:02.223Z
---

# PHP

## Code

### Attributes

- <https://jolicode.com/blog/ce-que-vous-devez-savoir-sur-les-attributes-de-php-8>

### Débug

- `var_dump`

### Typage

| Type | Description | Version PHP
|--|--|--
| int | Nombre entier | 7.0
| float | Nombre à virgule | 7.0
| string | Chaine de caractère | 7.0
| bool | Booléen valeur vrai ou faux possible | 7.0
| false | Booléen valeur faux uniquement | 8.0 (avec opérateur union) et 8.2 (type seul)
| true | Booléen valeur vrai uniquement | 8.2
| null | Vide | 8.0 (avec opérateur union) et 8.2 (type seul)
| array | Tableau | 7.0
| iterable | Objet itérable | 7.1
| callable | Toute methodes ou chose "appelable" | 7.0
| objet | Tout type d'objet | 7.2
| *Nom de classes ou interface* | Nom des classes & interface | 7.0
| self | Le type de l'instance courante | 7.0
| parent | Le type du parent courant | 7.0
| resource | Utilisé pour gérer des classes PHP anciennes | 8.1
| mixed | Tout les types | 8.0

Types spéciaux :

| Type | Description | Version PHP
|--|--|--
| never | Pour méthodes/fonctions : ne retournera aucune valeur et générera une exception ou se terminera avec un `die` ou `exit`.

Il est possible d'additionner les types avec l'opérateur **union** *(php 8.0)* :

```php
public function foo(Foo|Bar $input): int|float {};
```

On peut également rendre nullable un type (comme `type|null`) :

```php
public function test(): ?int {};
```

### Procédurale

#### Exceptions

#### Fonctions anonymes

##### Simple

```php
$addition = function(int $nombre1, int $nombre2) { return $nombre1 + $nombre2; }
# Ou avec retour à la ligne
$addition = function(int $nombre1, int $nombre2) {
  return $nombre1 + $nombre2;
}
```

##### Fléché

La même mèthodes que précédament :

```php
$addition = fn(int $nombre1, int $nombre2) => $nombre1 + $nombre2;
```

### Orienté objet


#### Espaces de nom

##### Classes globales PHP

Permet d'obtimiser les performances en précisant à PHP où chercher.

```php
<?php

namespace Test;

use \Exception; // Chercher dans l'espace global avec "\"
use \DateTime;
```

##### Fonctions globales PHP

Permet d'obtimiser les performances en précisant à PHP où chercher.

```php
<?php

namespace Test;

use function \round;
// Dit à PHP qu'on utilise la fonction round on peut les mettre tous sur une ligne avec des virgules
```

#### Classes

##### Exemple

```php
<?php

class Point
{
  public int $x;
  public int $y;
  public int $z;
  
  public function __construct(int $x = 0, int $y = 0, int $z = 0, )
  {
    $this->x = $x;
    $this->y = $y;
    $this->z = $z;
  }
}
```

##### Methodes spéciales

- `__toString()`
- `__construct()`

##### Mot clé `final`

Permet d'interdire l'heritage de classes / interfaces ou d'intérdire la surchage de constantes.

```php
final public class Foo {
    final public const TEST = '1';
}
```

#### Interface

```php
interface UnitEnum {
    public static function cases(): array;
} 
```

### Enumérations

Introduit dans PHP 8.1.

```php
enum Vetement {
  case Pantalon;
  case Chemise;
  case Chaussette;
  case Chapeau;
}

function acheterVetement(Vetement $vetement) {}

acheterVetement(Vetement::Pantalon) {}
acheterVetement(Vetement::Chemise) {}
acheterVetement(Vetement::Chaussette) {}
```

### Méthodes et class PHP

#### `array_map`

- <https://tainix.fr/article-technique/array_map-en-PHP-mode-d-emploi-et-utilisation-avancee>

## Outils

### Composer

<https://www.kaherecode.com/tutorial/le-guide-du-debutant-composer>

#### Initialiser un projet

```bash
composer init
```

#### Initialiser un projet en installant une dépendance

```bash
composer install ...
```

#### Gérer les dépendances

##### En production et développement

```bash
composer require ...
```

##### Uniquement en développement

```bash
composer require-dev ...
```

#### Astuces : composer sous windows manuellement

```powershell
function composer { php  C:\Chemin\du\repertoire\composer $args }
```

## Sécurité

### Attaque XSS

```php
htmlspecialchars($variable_echaper);
```