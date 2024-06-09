---
title: Husky
description: 
published: true
date: 2024-06-09T23:07:50.746Z
tags: 
editor: markdown
dateCreated: 2024-06-09T23:07:50.746Z
---

# Husky

- <https://github.com/typicode/husky>
- <https://typicode.github.io/husky>

## Installation

```bash
npm install husky --save-dev
npx husky install
npm pkg set scripts.prepare="husky install"
```

Le fichier `package.json` devrait contenir l'information suivante :

```json
// package.json
{
  "scripts": {
    "prepare": "husky install"
  }
}
```

## Utilisation

### Ajouter un hook

Utiliser la commande suivant :

```bash
husky add <file> [cmd]
```

#### Exemple

Par exemple pour executer la commande `npm test` à executer avant chaque commit :

```bash
npx husky add .husky/pre-commit "npm test"
git add .husky/pre-commit
```

Maintenant, tester avec un commit :

```bash
git commit -m "Keep calm and commit"
```

## Outils intégrables

### lint-staged
- <https://github.com/okonet/lint-staged>

#### Installation

```bash
npm install lint-staged --save-dev
npx husky add .husky/pre-commit "npx lint-staged"
```

#### Configuration

Possible dans plusieurs fichiers :

- `lint-staged` object in your `package.json`
- `.lintstagedrc` file in JSON or YML format, or you can be explicit with the file extension:
  - `.lintstagedrc.json`
  - `.lintstagedrc.yaml`
  - `.lintstagedrc.yml`
- `.lintstagedrc.mjs` or `lint-staged.config.mjs` file in ESM format
  - the default export value should be a configuration: `export default { ... }`
- `.lintstagedrc.cjs` or `lint-staged.config.cjs` file in CommonJS format
  - the exports value should be a configuration: `module.exports = { ... }`
- `lint-staged.config.js` or `.lintstagedrc.js` in either ESM or CommonJS format, depending on
  whether your project's _package.json_ contains the `"type": "module"` option or not.
- Pass a configuration file using the `--config` or `-c` flag

```json
// package.json
{
  "lint-staged": {
    "*": "your-cmd"
  }
}
```

```json
// .lintstagedrc
{
  "*": "your-cmd"
}
```

##### Exemple

```json
{
  "*.ts": "eslint",
  "*.md": "prettier --list-different"
}
```

```json
{
  "*.ts": ["prettier --list-different", "eslint"],
  "*.md": "prettier --list-different"
}
```

```json
{
  "*": "prettier --write",
  "*.ts": "eslint --fix"
}
```

### ESLint

Voir [ESLint](https://wiki.akipe.fr///books/developpement-informatique/page/eslint).

```json
// package.json
{
  "lint-staged": {
    "*.{js,ts,json}": "eslint --fix"
  }
}
```

### Prettier

Voir [Prettier](https://wiki.akipe.fr///books/developpement-informatique/page/prettier).

Il faut au préalable configurer **lint-staged**.

Ajouter cette configuration dans le fichier `package.json` :

```json
// package.json
{
  "lint-staged": {
    "**/*": "prettier --write --ignore-unknown"
  }
}
```

ou :
```json
// package.json
{
  "lint-staged": {
    "*.{js,ts,css,md,html,json}": "prettier --cache --write"
  }
}
```

### JestJS

Pour éxecuter la commande `npm test` avant chaque commit :

```bash
npx husky add .husky/pre-commit "npm test"
```
