---
title: dotenv
description: 
published: true
date: 2024-06-09T23:09:16.496Z
tags: 
editor: markdown
dateCreated: 2024-06-09T23:09:16.496Z
---

# dotenv

- <https://github.com/motdotla/dotenv>
- <https://www.npmjs.com/package/dotenv>

## Installation

```bash
npm install dotenv --save
```

## Utilisation

### Fichier `.env`

Créer un fichier `.env` :

```ini
# .env
VARIABLE_1="contenu de la variable"
VARIABLE_2=000001
```

### Récupérer les variables

#### JavaScript

Pour vérifier l'ensemble des variables :

```js
require('dotenv').config()

console.log(process.env)
```

Javascript simple :

```js
require('dotenv').config()

let var1 = process.env.VARIABLE_1
let var2 = process.env.VARIABLE_2
```

Avec ES6 (voir <https://github.com/motdotla/dotenv#how-do-i-use-dotenv-with-import>) :

```js
import * as dotenv from 'dotenv'

dotenv.config()

let var1 = process.env.VARIABLE_1
let var2 = process.env.VARIABLE_2
```
