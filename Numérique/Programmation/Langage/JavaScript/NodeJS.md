---
title: NodeJS
description: 
published: true
date: 2024-05-21T14:44:54.914Z
tags: 
editor: markdown
dateCreated: 2024-05-21T14:40:21.415Z
---

# NodeJS

- [https://nodejs.org/en/](https://nodejs.org/en/)
- <https://nodejs.org/en/download>

LTS : Long Term Support

> Version du logiciel avec prise  en charge des mises à jours sur le long terme, par rapport à une version "classique", avec notamment des mises à jour de sécurité et des corrections de bogues.

## Commandes


### Executer une application

```bash
# Executer un programme Node.js
node my_http.js
```

### Installer une dépendance (npm)

- Création d'un manifeste pour notre application

```bash
npm init
```

- Installer une bibliothèque nodejs

```bash
npm install express # Installation de express
npm install express --save # Sauvegarder en temps que dépendance
```

## Exemple de code

Un petit script qui affiche un message de bienvenu au nom envoyé en argument au script. Script à executer en local.

```js
#!/usr/bin/env node
'use strict';

let username = process.argv[2]; // Récupérant le premier argument (nommé "username") lors de l'execution du script 

if (!username) { // Si l'argument n'est pas spécifié, on va généré une erreur
    let appName = process.argv[1].split(require('path').sep).pop();
    console.error('Missing argument! Example: %s YOUR_NAME', appName);
    process.exit(1);
}

// Si l'argument a bien été spécifié :
console.log('Salut %s !', username); // On affiche le message de bienvenu avec l'argument

```

Un petit serveur web avec une simple page qui affiche : *"Bravo! Tu es sur un serveur http nodejs."*

```js
const http = require('http');

// On va créer un serveur http qui va recevoir les requêtes web
http.createServer((request, response) => {

    // On défini le header de la requête
    response.writeHead(200, {
        'Content-Type': 'text/plain'
    });

    // On défini ensuite le contenu de la page
    response.write('Bravo! Tu es sur un serveur http nodejs. \n');

    // On termine la page
    response.end();
}).listen(7777); // On spécifie sur quel port le serveur http sera executé

```