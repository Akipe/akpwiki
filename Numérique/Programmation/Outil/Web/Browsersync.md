---
title: Browsersync
description: 
published: true
date: 2024-05-21T18:10:33.222Z
tags: 
editor: markdown
dateCreated: 2024-05-21T18:10:33.222Z
---

# Browsersync

Permet la synchronisation entre différents appareils lors de l'affichages de pages web. Il permet également de mettre à jour dynamiquement la page web (F5) lors de modifications de ressources statiques.

- <https://browsersync.io/>
- <https://github.com/BrowserSync/browser-sync/>
- <https://browsersync.io/#install>

## Installation

```shell
npm install browser-sync
```

## Commandes

### Démarrage

#### Site web statique (mode serveur)

```shell
npx browser-sync start --server
```

#### Site web dynamique (mode proxy)

```shell
npx browser-sync start --proxy "myproject.dev"
```

### Rafraichir la page automatiquement

Avec l'options `--file`. Fonctionne quelque soit le mode utilisé (proxy ou serveur).

Dans l'exemple suivant, on rafraichi la page dès qu'un fichier `.css` dans le dossier `css/` est modifié : 

```shell
npx browser-sync start --server --files "css/*.css"
```

## Ressources

- <https://browsersync.io/docs>
- <https://browsersync.io/docs/command-line>