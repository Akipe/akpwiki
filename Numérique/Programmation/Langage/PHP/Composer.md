---
title: Composer
description: 
published: true
date: 2024-05-21T14:12:07.306Z
tags: 
editor: markdown
dateCreated: 2024-05-21T14:10:12.442Z
---

# Composer

- <https://www.kaherecode.com/tutorial/le-guide-du-debutant-composer>

## Installation

## Commandes

### Initialiser un projet

```bash
composer init
```

### Initialiser un projet en installant une dépendance

```bash
composer install ...
```

### Gérer les dépendances

#### En production et développement

```bash
composer require ...
```

#### Uniquement en développement

```bash
composer require-dev ...
```

### Astuces : composer sous windows manuellement

```powershell
function composer { php  C:\Chemin\du\repertoire\composer $args }
```

## Example

```json
{
  "name": "nom/projet",
  "description": "PHP client library for Network Ups Tools (NUT)",
  "type": "library",
  "keywords": ["nut", "network ups tools", "ups"],
  "license": "MIT",
  "authors": [
    {
      "name": "Nom prénom",
      "role": "Developer"
    }
  ],
  "require": {
    "php": ">=8.1"
  },
  "autoload": {
    "psr-4": {
      "Lepidoptaire\\": "src/"}
  }
}
```
