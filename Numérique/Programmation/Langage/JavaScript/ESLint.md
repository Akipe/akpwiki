---
title: ESLint
description: 
published: true
date: 2024-06-09T23:08:25.273Z
tags: 
editor: markdown
dateCreated: 2024-06-09T23:08:25.273Z
---

# ESLint

Outil d’analyse de code statique permettant d’identifier des erreurs dans du code JavaScript.

- <https://eslint.org/>

## JavaScript

## TypeScript

- <https://typescript-eslint.io/>
- <https://github.com/typescript-eslint/typescript-eslint>

### Installation

```bash
npm install --save-dev \
	@typescript-eslint/parser \
    @typescript-eslint/eslint-plugin \
    eslint \
    typescript
```

### Configuration

Ajouter la configuration pour ESLint (sans TypeScript) :

```

```

Créer le fichier `.eslintrc.cjs` ou `eslintrc.json` à la racine du projet (si le projet n'utilise pas ESM, on peut également le nommé `.eslintrc.js`) :

```js
// .eslintrc.json
/* eslint-env node */
{
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/recommended"
  ],
  "parser": "@typescript-eslint/parser",
  "plugins": ["@typescript-eslint"],
  "root": true,
  "parserOptions": {
    "parser": "@typescript-eslint/parser",
    "project": ["tsconfig.json"]
  },
  "ignorePatterns": ["dist/*", "*.js"]
}

```

#### Template de configurations

Voir <https://github.com/typescript-eslint/typescript-eslint/tree/main/packages/eslint-plugin/src/configs> & <https://typescript-eslint.io/linting/configs>.

```json
{
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/recommended",
    "plugin:@typescript-eslint/recommended-requiring-type-checking",
    "plugin:@typescript-eslint/strict",
    "plugin:@typescript-eslint/eslint-recommended"
  ],
}
```

### Commande

#### Vérifier

Executer la vérification :

```bash
npx eslint .
```

#### Vérifier et essayer de corriger

```bash
npx eslint --fix .
```

## Configurations communes

### Vérifier avant chaque commit

Voir [Husky](https://wiki.akipe.fr///books/developpement-informatique/page/husky).

### Template de configurations

#### Prettier

Permet l'intégration avec Prettier en désactivant certaines régles non compatibles.

<https://github.com/prettier/eslint-config-prettier>

##### Installation

```bash
npm install --save-dev eslint-config-prettier
```

Puis ajouter le template de configuration `prettier` dans le fichier de configuration `.eslintrc.json` :

```json
{
  "extends": [
    "...",
    "prettier"
  ],
}
```

##### Vérifier la compatibilité

Avec l'outil `eslint-config-prettier` :

```bash
npx eslint-config-prettier path/to/main.js
```
