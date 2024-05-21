---
title: Visual Studio Code
description: 
published: true
date: 2024-05-21T18:23:29.502Z
tags: 
editor: markdown
dateCreated: 2024-05-21T18:23:29.502Z
---

# Visual Studio Code

Egalement appelé ***"vscode"***.

## Extensions

### Communs

#### Organisation du code

- **Better Comments**  

Permet de mettre en surbrillance de type TODO, FIXME, les params et certains aux mots-clés dans les commentaires dans des différents langages.

- **~~Bracket Pair Colorizer 2~~**  

Permet de mettre en couleurs correspondantes les accolades dans le code afin de mieux repérer les blocs de code.  
Remplacé par une configuration dans `settings.json` :

```json
{
    "editor.bracketPairColorization.enabled": true,
    "editor.guides.bracketPairs":"active"
}
```

- **indent-rainbow**  

Colorise les indentations pour mieux cerner à quel niveau où l'on se situe à un emplacement du code.

- **? Path Intellisense ?**  

Pour autocompléter les noms des fichiers.

- **vscode-icons**  

Permet d'ajouter des îcones aux fichiers et dossiers qui sont dans l'explorateur de VSCode, rendant l'identification des types de fichiers/dossiers bien plus rapides.

- **Prettier**  

Prettier is an opinionated code formatter that works particularly well if you have multiple people working on a single project, because the extension enforces a consistent style.  

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

- **Live Share**
- **Project Manager**
- **EditorConfig for VS Code**  

Permet d'utilisation la convention de nommage à partir du fichier `.editorconfig` du projet : <https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig>

#### Accés distant

- **Remote Development**

Un pack d'extension de Microsoft permettant d'ouvrir un dossier depuis une source distante, que ce soit un conteneur Docker, un serveur (via SSH) ou WSL. Indispensable quand on a l'habitude de développer dans les conteneurs.

- **Remote - SSH**
- **Dev Containers**
- **WSL**

#### Regex

- **Regex Previewer**  

Regular expressions can be quite the puzzle to get right. Regex Previewer gives you a side document that matches your regex.

#### Correcteur orthographique

- **Code Spell Checker**  

Un simple spell checker pour mettre en avant les typos sur les mots anglais qui sont courants dans le code.

- **French Réforme 90 - Code Spell Checker**

#### Git

- **GitLens**  

Permet d'avoir une gestion complète de git sous VSCode ainsi que l'indication ligne par ligne de quel commit provient une ligne de code en direct sur l'espace de travail.

- **Git History**

Similar to GitLens, Git History is a VSCode extension that gives a visual of the git log. No longer should you look through git log in the terminal.

#### Web

- **Live Server**  

Live Server launches a local development server with a live reload feature both for static and dynamic pages.

- **Debugger for Firefox**  

For debugging with firefox

- **REST Client**  

##### CSS

- **CSS Peek**  

This extension is invaluable for front-end developers. Inspired by a similar feature in the IDE Brackets, CSS Peek allows you to extend your HTML and ejs file to show CSS/SCSS/LESS code within the source code.

- **Colorize**  

Sticking with colors, Colorize instantly visualizes CSS colors in your CSS/SASS/Less/... files. This makes it very easy to see at a glance which colors you’re using where.

##### JS

- **JavaScript Code Snippets**  

While VSCode includes built-in JS IntelliSense, JS Code Snippets enhances that experience by adding a slew of import/export triggers, class helpers, and method triggers. The extension supports JS, TypeScript, JS React, TS React, HTML, and Vue

### Theme

- **GitHub Sharp Dark**
- **Dracula Theme**

### Base de donnée

- **SQLTools**
- **SQLTools PostgreSQL**
- **SQLTools SQLite**

### PHP

- **PHP Intelephense**  

Disable the built-in VSCode PHP Language Features.

1. Go to Extensions.
2. Search for @builtin php
3. Disable PHP Language Features. Leave PHP Language Basics enabled for syntax highlighting.

Note that other (3rd party) PHP extensions which provide similar functionality should also be disabled for best results.

Add glob patterns for non standard php file extensions to the files.associations setting.

For example: "files.associations": { "*.module": "php" }.

Optionally purchase and enter your licence key by opening the command pallete -- ctrl + shift + p -- and searching for Enter licence key.

- **PHP DocBlocker**  

Permet d'autogénérer le texte des commentaires longs en PHP (@var, @return, param, etc...)

- **PHP getters and setters**  

Permet de générer les getters et les setters des propriétés PHP dans les classes.

- **PHP Namespace Resolver**  

Permet d'importer la classe ciblée dans la classe en cours (au lieu de l'écrire manuellement et de faire éventuellement une faute de frappe).

- **PHPStan**  

Analyse automatiquement le code à chaque modification d'un fichier pour savoir s'il est valide avec les règles que vous avez configuré, permettant d'obtenir une qualité de code bien plus élevée qu'habituellement usuellement.

- **PHP import checker**  

This extension provides an easy way to keep your code clean and organized. In a large project, there will be a lot of file imports and sometimes it becomes hard to check which files are used and which are not. This extension will let you know when a given class is imported but not used. You can also customize the color.

- **PHP Debug**  

This one is simple enough to explain but is really powerful. PHP Debug is a PHP Debugger. 

- PHP Tools ?

#### Symfony

- **Twig Language 2**  

Ajoute la coloration syntaxique et quelques snippets pour le langage Twig.

- **YAML**
- **DotEnv Official + Vault**  

La coloration syntaxique pour les fichiers .env

### VueJS (3)

- **Volar**
- **TypeScript Vue Plugin (Volar)** (`Vue.vscode-typescript-vue-plugin`)

### TypeScript

### C#

- **C#**

### Makefile

- Makefile Tools <https://marketplace.visualstudio.com/items?itemName=ms-vscode.makefile-tools>

## Paramétre

### Optimisation

#### Emmet pour d'autre types de fichier

Rechercher le paramètre "emmet"

Il faut ici indiquer que lorsque nous travaillons sur un fichier TWIG, celui-ci devra se formater automatiquement en HTML.

```twig -> html```

#### Couleur par paire de bracket

```json
{
    "editor.bracketPairColorization.enabled": true,
    "editor.guides.bracketPairs":"active"
}
```

## Raccourcies claviers

### Générale

- Afficher tous les raccourcies claviers :  

`CTRL` + `K` `CTRL` + `S`

### Code

- "replier" tout le code :  

`CTRL` + `K` `CTRL` + `0`

- replier le code au niveau 1 :  

`CTRL` + `K` `CTRL` + `1`

- déplier tout le code :  

`CTRL` + `K` `CTRL` + `J`