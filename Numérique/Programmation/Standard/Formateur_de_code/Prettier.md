---
title: Prettier
description: 
published: true
date: 2024-05-21T18:01:52.168Z
tags: 
editor: markdown
dateCreated: 2024-05-21T18:01:52.168Z
---

# Prettier

Formateur de code dogmatique.

- <https://prettier.io/>
- <https://prettier.io/docs/en/index.html>

## Installation

```bash
npm install --save-dev --save-exact prettier
```

## Configuration

Créer le fichier de configuration, vide, pour gérer la configuration (`.prettierrc.json`) :

```json
// .prettierrc.json
{}
```

Créer le fichier pour ignorer certains type de fichier à la vérification (se baser sur gitignore) (`.prettierignore`) :

```bash
# .prettierignore
# Ignore artifacts:
build
coverage
```

Liste de configurations : <https://prettier.io/docs/en/configuration.html>


## Commandes

### Vérifier si le code respect la mise en page

```bash
npx prettier --check .
```

### Réécrire le code en le faisant correspondre à la mise en page

```bash
npx prettier --write .
```

## Intégration

### Avant chaque commit

Voir [Husky](https://wiki.akipe.fr///books/developpement-informatique/page/husky).

### ESLint

Voir [ESLint](https://wiki.akipe.fr///books/developpement-informatique/page/eslint).

## Utilitaires

### Editeurs

- <https://prettier.io/docs/en/editors.html>
- vscode : <https://github.com/prettier/prettier-vscode>
- JetBrains : <https://prettier.io/docs/en/webstorm.html>