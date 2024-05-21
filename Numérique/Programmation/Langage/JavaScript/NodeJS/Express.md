---
title: Express
description: 
published: true
date: 2024-05-21T14:50:54.929Z
tags: 
editor: markdown
dateCreated: 2024-05-21T14:50:54.929Z
---

# Express

Express est un framework Node.js pour développer rapidement des sites web.

## Installation

### Installation manuel

```bash
npm install express
```

Voici un exemple d'utilisation du framework express :

```javascript
const express = require('express'); // On charge express
const hello_world = express(); // On créer une application web, appelé "hello_world"
const port = 3000; // L'application web sera accessible en localhost sur le port 3000

// On créer notre première pas à l'url root '/'
hello_world.get('/', (req, res) => {
    res.send('Hello World!'); // Contenu de notre première page
});

// On démarre notre application web en "écoutant" sur le port défini plus haut,
// On affiche également un message dans le terminal pour prévenir l'utilisateur que l'app est éxecuté sur le port 3000
hello_world.listen(port, () => {
    console.log(`Example app listening on port ${port}`);
});

```

### Utilisation du générateur

Le générateur permet de créer simplement un squelette d'application depuis le terminal avec des questions rapide.

On commence par installer le générateur :

```bash
npm install express-generator -g # -g pour l'installer de manière générale
```

Pour afficher l'aide :

```bash
express -h
```

### Installation depuis le générateur

La commande va créer un dossier NOM_APPLICATION avec la base du code.

```bash
express --view=pug NOM_APPLICATION # Génération du projet Express
cd NOM_APPLICATION # On entre dans le dossier contenant le projet
npm install # On installe les dépendances
```

```bash
DEBUG=NOM_APPLICATION:* npm start # MacOS et Linux
set DEBUG=NOM_APPLICATION:* & npm start # Windows
```

L'application web est accessible par défaut sur le port **3000** : [http://hôte_local:3000/](http://hôte_local:3000/)

Voici l'arborescence de base de votre application :

```
.
├── app.js
├── bin
│   └── www
├── package.json
├── public
│   ├── images
│   ├── javascripts
│   └── stylesheets
│       └── style.css
├── routes
│   ├── index.js
│   └── users.js
└── views
    ├── error.pug
    ├── index.pug
    └── layout.pug
```

## Routage

Le routage permets de définir la relation entre les urls (les chemin, requêtes HTTP GET, POST...) du site web avec les controlleurs (bout de code permettant de réaliser des actions en fonction de l'utilisateur).

```javascript
app.METHOD(PATH, HANDLER);
// app : instance d'express
// METHOD : méthode requête HTTP comme GET, POST...
// PATH : chemin spécifié dans l'URL
// HANDLER : fonction à exécuter quand la route correspond
```

## Principe MVC : Modèle vue controlleur

## Node

### Présentation

Détourner le langage JS en langage server. Le moteur JS dans Node est le même que celui de Chromium : V8.

Electron, framework pour application desktop, tourne sous electron.

Patterne MVC : Modèle Vue Controlleur.

### Initier une application

Modules sont géré par https://www.npmjs.com/ et npm. Npm permet de gérer les dépendances Nodes

Initialiser une application :

```bash
npm init
```

Un fichier `package.json` sera générer et contient la description et la liste des dépendances de notre application.

```bash
npm install NOM_MODULE
```

Il ne faut pas enregistrer auprès de Git les modules du projet (dans le dossier node_modules). Il suffira de lancer la commande `npm install`.

Pour ce faire on créer un fichier .gitignore :

```gitignore
node_modules # On ne prend pas en charge le dossier
```

Démarrer une application :

```bash
node app.js
```

On peut définir des commandes node dans notre manifeste, à la section "scripts" :

```json
"scripts": {
    "start": "node app",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
```

On peut ensuite executer la commande :

```bash
npm run start # Exécute la commande "node app"
```

### Nodemon

Permet de surveiller un projet node pour le relancer en cas de modification du code source.

```bash
npm install -g nodemon

nodemon app.js # au lieu de "node app.js"
```

## Express

### Présentation

Bibliothéque JS qui permet de créer un serveur web.

Documentation officiel : [http://expressjs.com/](http://expressjs.com/)

### Installation

```bash
npm install express
```

Exemple de base :

```js
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
```

### Importation / Exportations

Similaire aux using en C# :

```js
const express = require('express') //Pour les applications
// ou pour les modules :
import express from 'express' // Uniquement pour les modules node, PAS les applications
```

### Commandes

#### Générer le projet

```bash
npx express-generator
# Ou
npm install -g express-generator
express
# avec pug
express --view=pug myapp
```

```bash
npm install
```

```bash
# MacOS et Linux
DEBUG=myapp:* npm start
# Windows CMD
set DEBUG=myapp:* & npm start
# Windows Powershell
$env:DEBUG='myapp:*'; npm start

```

Express utilise son propre serveur web :

```js
// app.listen : on va "écouter" sur un port (3000)
app.listen(3000, () => {
    // ...
})
```

### Gérer des pages

```js
app.get('/route', (req, res) => {
    res.send('A propos')
})
```

Les marqueurs de route commences par `:` : `:name`.

```js
app.get('/hello/:name/edit/:id', (req, res) => {
    let name = req.params.name // req.params.name récupére ':name'
    let id = req.params.id // req.params.id récupére ':id'
})
```

### Verbes HTTP

Tableau : get et post

Valeurs simple : get post put delete

#### Get

Récupérer une page ou en API un élément.

```js
// req : requette, créer par express avec toutes infos de la requette
// res : response, réponse à la requette
// next : pour un enchainement de requettes
app.get('/', (req, res) => {

})
```

#### Post

Formulaire et ajout d'un éléments en API

#### Put

API : mettre à jour

**patch** : mettre à jour certains éléments d'un document : on envoie que les éléments à changer

**put** : servait à remplacer un document par un autre : on envoit donc toutes les données dans le put, notamment les éléments non modifiés

#### Delete

API : supprimer un élément

### Bodyparser

Module Nodejs qui permet d'analyser le corp d'une requete, quel que soit le verbe utilisé.

```bash
# Dépreciser, utiliser express
#npm install body-parser
```

```js
const express = require('express')

app.use(express.urlencoded({extended: true}))
```

### Middlewares

Pour chacune de mes routes, j'aimerai afficher le chemin dans le terminal : utilisation d'un middleware.

bout de code qui s'executeront à un événement défini, par exemple sur expressjs par rapport aux routes.

Elle s'executeront selon le contexte.

Associé à un chemin : executer uniquement sur le chemin
Non associé : executer sur toutes les routes.

Il est important de définir les middlewares avant la définition des pages, car elle seront executé avant.

```js
app.use((req, res, next) => { // Création du middleware
    
    next() // Tu passe à la fonction middleware suivante ou à la route
})
```

### Routeur

Il doit mettre en relation un chemin (url) du site avec un controlleur.

Possible de les définir dans un autre fichier pour une meilleures organisation, dans une dossier "/routes/index.js" et en plusieurs fichiers.

```js
// /routes/index.js
const express = require("express")
const router = express.Router() // On récupére le routeur d'express

router.get('/', (request, response) => {
    response.send("Accueil") // On envoie le contenu de la réponse
                             // c'est à dire la page à afficher
})

router.get('/about', (req, res) => {
    res.send('A propos')
})

// sur l'entrée :name sera appliqué la fonction "trim"
router.get('/hello/:name', (req, res) => {
    let name = req.params.name // On récupére le marqueur "name" de la route
    res.send(`Hello ${name} !`)
})


/* première posibilité */
// dans /app.js
require('./routes') // Si index.js
// similaire à
require('./routes/index.js')

/* deuxième posibilité */

// dans /routes/index.js
module.exports = router

// dans /app.js
const router = require('./routes')


/* ensuite on indique vouloir utiliser les routes*/
app.use('/' router) // "/" correspond au chemin sur lequel on appliques les routes
```

Définir une route par défaut : il faut la spécifier après toutes les autres routes.

```js
router.all('', (req, resp) => {}) // Possibilité de mettre des Regex et des jockers
router.all('*', (req, res) => {
    res.status(404).send("Erreur 404: page non trouvé")
})
```

#### Fichiers statiques

Il faut indiquer quels fichiers statiques on autorise avec Express.

```js
app.use('/public', express.static(__dirname + '/public'))
// premier argument correspond au chemin URL virtuel sur lequel on souhaite définir l'accés aux ressources
// __dirname correspond au chemin du fichier actuelle
// on rajoute le dossier contenant les ressources
```

### Controlleurs

Il met en relation les données avec les vues.

C'est le code qui prend en charge la requette et la réponse aproprié : "Un chemin améne à une fonction".

Ils ne contiennent que des fonctions de rappelles.

On suffixe les contolleurs par "Controller", ex: "homeController.js"

Utilisable avec les classes ou en mode Nodejs :

```js
// Orienté classe, utilisable dans d'autre contexte

class HomeController {

    index(req, res) {
        res.send("Accueil du controlleur")
    }
}

module.exports = new HomeController(); 
```

```js
// Utilisable uniquement en Nodejs

exports.index = (req, res) => {
    res.send("Accueil du controlleur")
}
```

### Base de données

Modèles : c'est un objet métier d'intérét, qui a de l'importance dans l'application.

Un modèle correspond à une table dans notre base de donnée. On fera le lien entre le modèle et la base de donnée

En MVC :  
DAO (classe d'accés aux données), les repository et les modèles.

La récupération des données de la BDD se réalise à partir des controlleurs, qui appélent des classes repository qui réalisent des crud dans la BDD.

#### SQLite

Pour utiliser SQLlite avec nodejs :
```bash
npm install sqlite3
```

https://www.npmjs.com/package/sqlite3

```js
// Fichier qui va charger la base de donnée SQLite
const path = require("path")
const sqlite3 = require('sqlite3')

const databasePath = path.join(__dirname, "data", "vote.db")

const database = new sqlite3.Database(databasePath, (err) => {
    if (err) {
        return console.error(`Erreur SQL : ${err}`)
    }
    console.log("Base de données connectée")
})

module.exports = database

```

#### Repository

Il gére l'interraction à la BDD d'une entité.

Un repository par table, qui s'occupe du crud de la table. On aura un repository par table.

Il existe des couches d'absctraction car les repository sont très similaires, on peut donc les simplifier (à voir prochainement).

On défini également les requêtes spécifique dans le repository (exemple : récupérer les nom commençant par une certaine lettre, etc).

Plusieurs variant de nommage des methodes :
- create
- get / select
- (get / select) all
- put
- delete

Lors d'un appel à la base de donnée, JS risque de se bloqué car il n'est pas multitache, il faut donc créer une fonction asynchrone qui permet de ne pas bloquer le reste de l'application.

On utilise les promesses : on ne sait pas quand la réponse se termine et si elle se réalisera correctement.

Classe DAO : Direct Access Object : à préciser.

```js
// candidatesRepository.js

// On importe les données de la BDD
const database = require('./index')

exports.getAll = () => {
    return new Promise((resolve, reject) => {
        database.all(
            "SELECT id, lastname, firstname, slogan FROM candidates", // Requete SQL
            [], // Parametres pour la requete SQL
            (err, rows) => { // Fonction exécuté lors du traitement
                if (err) {
                    console.error('Erreur SQL : ' + err)
                    reject(err)
                } else {
                    resolve(rows)
                }
            }
        )
    })
}

exports.getById = (id) => {
    database.all(
        "SELECT id, lastname, firstname, slogan FROM candidates WHERE id=?", // Requete SQL
        [id], // Parametres pour la requete SQL
        (err, rows) => { // Fonction exécuté lors du traitement
            if (err) {
                console.error('Erreur SQL : ' + err)
                reject(err)
            } else {
                resolve(rows)
            }
        }
    )
}

exports.create = (model) => {}

exports.update = (model) => {}

exports.delete = (id) => {}

```

Pour les requetes préparé en SQLite 3 :

```js
database.all(
    "SELECT id, lastname, firstname, slogan FROM candidates WHERE id=?", // id=? récupére l'id dans les paramètres
    [id], // Parametres envoyé à la requete SQL
    (err, row) => { // Fonction de traitement

    }
)
```

### ORM

Object relation mapper.

Sur nodejs, le plus connu est Sequelize [https://sequelize.org/](https://sequelize.org/).

### Les vue

#### LiquidJS

[https://liquidjs.com/](https://liquidjs.com/)

```bash
npm install liquidjs
```

```js
const { Liquid } = require('liquidjs')
const path = require('path')

const viewPath = path.join(__dirname, '../', 'view')

const viewEngine = new Liquid({
    root: viewPath, // Répértoire où chercher les vues
    extname: '.html'
})

// Sans l'application
//module.exports = viewEngine

// Avec l'application
// pour avoir accés à l'instance d'ExpressJS
module.exports = (app) => {
    // Créer l'instance de l'app de gestion de vue
    const viewEngine = new Liquid({
        root: viewPath, // Répértoire où chercher les vues
        extname: '.html' // Nos fichier liquidjs auront l'extension .html (coté liquijs)
    })
    
    // On précise à ExpressJS qu'il faudra executer viewEngine (liquidjs) pour les fichier .html
    app.engine('html', viewEngine.express())
    // Le moteur de vue principal sera celui défini pour les fichiers d'extension .html
    app.set('view engine', 'html')
}
```

### Postman

Outil pour tester les requetes vers les API.
[https://www.postman.com/downloads/?utm_source=postman-home](https://www.postman.com/downloads/?utm_source=postman-home)

### Autre

Pour définir une valeur par défaut en JS :

```js
let name = variable_maybe_null ?? "toto"
```

L'utilisation des `use` de express sont insensible à l'ordre.

__dirname : correspond au repertoire du fichier actuelle.

Si on ne termine pas les requetes (avec `res.end()`) le navigateur attendra la fin de la requete. 

#### Trim

Supprime les espaces en début et fin de chaine de caractère.

#### Destructuration

```js
const { id } = req.params
// similaire à
const id = req.params.id

const { id, name } = req.params
// ==
const id = req.params.id
const name = req.params.name
```


### Générateur de base express

## Node

### import/ exportation

#### Fonction

```js
exports.functionA = () => {}
exports.functionB = (id) => {}
exports.functionC = (model) => {}
// ==
module.exports = {
    functionA(id) {

    },

    functionB(model) {

    },

    functionC() {

    }
}
```

#### Class

```js
class Test {}

// Export de la classe
module.exports = Test;
// Export d'une instance
module.exports = new Test();
```

#### Importation

```js
require('./mon/fichier')
let parametre
require('./mon/fichier')(parametre)
```

## MVC

[![Modèle-vue-contrôleur_(MVC)_-_fr.png](https://wiki.akipe.fr///uploads/images/gallery/2022-04/scaled-1680-/1BKyu6emfdMJLmh2-modele-vue-controleur-mvc-fr.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-04/1BKyu6emfdMJLmh2-modele-vue-controleur-mvc-fr.png)

## TLDR

### Arborescence

```
app/
    controllers/                    # Controleurs
        ...
    db/                             # Base de données
        data/                       # Stockage de la base de donnée
            example.db              # ex: sqlite
        candidatesRepository.js     # Repository de l'entité
        index.js                    # Chargement de la base de donnée
    node_modules/                   # Ensemble des bibliothèques externes
    public/                         # Fichiers statiques
        assets/
            css/
            js/
            ...
    routes/                         # Ensemble de la configuration des routes
        index.js
        ...
    app.js                          # Point d'entrée de notre site
    package-lock.json
    package.json                    # Configuration de notre site
```

```bash
npm install express-generator -g
express
npm install
```

Avec typescript

```bash
npm install --save-dev typescript
npm install --save-dev @types/express
```

### Express validator

```bash
npm install express-validator
```

Utilisation directement dans le routeur :

```js
const { body, validationResult } require('express-validator')

router.post(
  '/ma-route',
  body('lastname')
  	.not().isEmpty().withMessage("Champ requis")
  	.isLength({min: 2}).withMessage("Taille minimal de 2")
  ,
  (req, res) => {
    let errors = validationResult(req)
    console.log(errors.array())
    // ...
  }
);
```

Utilisation dans un routeur :

***(En chainant)***

```js
// middlewares/validator.js
const { body } = require('express-validator')

exports.candidateValidator[
	body('lastname')
  		.not().isEmpty().withMessage("Champ requis")
  		.isLength({min: 2}).withMessage("Taille minimal de 2"),
  	body('firstname').not().isEmpty().withMessage("Champ requis")
]
```

```js
// routes/index.js
const validator = require('../middlewares/validator')

router.post("url", validator.candidateValidator, nomController.action);
```

***(avec un CheckSchema)***

```js
// form/candidateValidator.js
const { checkSchema } = require('express-validator')

// https://express-validator.github.io/docs/schema-validation.html
module.exports = checkSchema({
    /*id: {
        isInt: true,
        toInt: true
    },*/
    firstname: { // Le champ est requis, aucun chiffre, autorise les espaces et les tirets "-".
        matches: {
            options: '^[a-zA-ZÀ-ÿ]+(-| )?[a-zA-ZÀ-ÿ]+$',
            errorMessage: "Le prénom ne doit contenir que des lettres."
        },
        notEmpty : {
            options: {
                ignore_whitespace: true
            },
            errorMessage: "Le prénom est requis"
        },
        isLength: {
            options: {
                min: 4,
                max: 24
            },
            errorMessage: "Le prénom doit être avoir entre 4 et 24 caractères."
        },
    },
})
```

```js
// routes/index.js
const candidateValidator = require('../form/candidateValidator')

router.post('/candidates/edit/:id', candidateValidator, candidateController.updatePost)
```

```js
// controller/nomController.js
const { validationResult } = require('express-validator')
// ...
const validationResult
action(req, res) {
  const validationErrors = validationResult(req)
  
  if (!validationErrors.isEmpty()) {
    console.log(validationErrors.array())
    res.render(
      'exemple_vue',
      {
        errors: validationErrors.array()
      }
    )
  } else {
    // C'est ok
  }
}
```

```html
<!-- vue/exemple_vue.html -->
{% for error in errors %}
<p class="danger">{{ error.param }} : {{ error.msg }}</p>
```

#### Type de données à tester

- req.body
- req.cookies
- req.params
- req.query

#### Type de vérification

```js
// express-validator/src/chain/validator.d.ts
not(): Return;
withMessage(message: DynamicMessageCreator): Return;
withMessage(message: any): Return;
custom(validator: CustomValidator): Return;
exists(options?: {
    checkFalsy?: boolean;
    checkNull?: boolean;
}): Return;
isArray(options?: {
    min?: number;
    max?: number;
}): Return;
isObject(options?: {
    strict?: boolean;
}): Return;
isString(): Return;
notEmpty(options?: Options.IsEmptyOptions): Return;
contains(elem: any, options?: Options.ContainsOptions): Return;
equals(comparison: string): Return;
isAfter(date?: string): Return;
isAlpha(locale?: Options.AlphaLocale, options?: Options.IsAlphaOptions): Return;
isAlphanumeric(locale?: Options.AlphanumericLocale, options?: Options.IsAlphanumericOptions): Return;
isAscii(): Return;
isBase32(): Return;
isBase58(): Return;
isBase64(options?: Options.IsBase64Options): Return;
isBefore(date?: string): Return;
isBIC(): Return;
isBoolean(options?: Options.IsBooleanOptions): Return;
isBtcAddress(): Return;
isByteLength(options: Options.MinMaxExtendedOptions): Return;
isCreditCard(): Return;
isCurrency(options?: Options.IsCurrencyOptions): Return;
isDataURI(): Return;
isDate(options?: Options.IsDateOptions): Return;
isDecimal(options?: Options.IsDecimalOptions): Return;
isDivisibleBy(number: number): Return;
isEAN(): Return;
isEmail(options?: Options.IsEmailOptions): Return;
isEmpty(options?: Options.IsEmptyOptions): Return;
isEthereumAddress(): Return;
isFQDN(options?: Options.IsFQDNOptions): Return;
isFloat(options?: Options.IsFloatOptions): Return;
isFullWidth(): Return;
isHalfWidth(): Return;
isHash(algorithm: Options.HashAlgorithm): Return;
isHexColor(): Return;
isHexadecimal(): Return;
isHSL(): Return;
isIBAN(): Return;
isIdentityCard(locale?: Options.IdentityCardLocale): Return;
isIMEI(options?: Options.IsIMEIOptions): Return;
isIP(version?: Options.IPVersion): Return;
isIPRange(version?: Options.IPVersion): Return;
isISBN(version?: number): Return;
isISSN(options?: Options.IsISSNOptions): Return;
isISIN(): Return;
isISO8601(options?: Options.IsISO8601Options): Return;
isISO31661Alpha2(): Return;
isISO31661Alpha3(): Return;
isISO4217(): Return;
isISRC(): Return;
isIn(values: readonly any[]): Return;
isInt(options?: Options.IsIntOptions): Return;
isJSON(options?: Options.IsJSONOptions): Return;
isJWT(): Return;
isLatLong(options?: Options.IsLatLongOptions): Return;
isLength(options: Options.MinMaxOptions): Return;
isLicensePlate(locale: Options.IsLicensePlateLocale): Return;
isLocale(): Return;
isLowercase(): Return;
isMagnetURI(): Return;
isMACAddress(options?: Options.IsMACAddressOptions): Return;
isMD5(): Return;
isMimeType(): Return;
isMobilePhone(locale: Options.MobilePhoneLocale | readonly Options.MobilePhoneLocale[], options?: Options.IsMobilePhoneOptions): Return;
isMongoId(): Return;
isMultibyte(): Return;
isNumeric(options?: Options.IsNumericOptions): Return;
isOctal(): Return;
isPassportNumber(countryCode?: Options.PassportCountryCode): Return;
isPort(): Return;
isPostalCode(locale: Options.PostalCodeLocale): Return;
isRgbColor(includePercentValues?: boolean): Return;
isRFC3339(): Return;
isSemVer(): Return;
isSlug(): Return;
isStrongPassword(options?: Options.IsStrongPasswordOptions): Return;
isSurrogatePair(): Return;
isTaxID(locale: Options.TaxIDLocale): Return;
isURL(options?: Options.IsURLOptions): Return;
isUUID(version?: Options.UUIDVersion): Return;
isUppercase(): Return;
isVariableWidth(): Return;
isVAT(countryCode: Options.VATCountryCode): Return;
isWhitelisted(chars: string | readonly string[]): Return;
matches(pattern: RegExp | string, modifiers?: string): Return;
```

#### Documentation

documentation : [https://github.com/validatorjs/validator.js#validators](https://github.com/validatorjs/validator.js#validators)

### Path

```js
const path = require('path')

const unChemin = path.join(__dirname, '../', 'views')
```

### Token CSRF

#### Avec `crypto`

```bash
npm i cookie-parser cookie-session
```

```js
var cookieParser = require('cookie-parser');
var cookieSession = require('cookie-session'); // require cookie session
var { randomBytes } = require('crypto');

/* Middleware */
app.use(cookieParser());

/* Coockie session */
// set up the cookie for the session
app.use(cookieSession({
  name: 'session',                              // name of the cookie
  secret: 'MAKE_THIS_SECRET_SECURE',            // key to encode session
  maxAge: 24 * 60 * 60 * 1000,                  // cookie's lifespan
  sameSite: 'lax',                              // controls when cookies are sent
  path: '/',                                    // explicitly set this for security purposes
  secure: process.env.NODE_ENV === 'production',// cookie only sent on HTTPS
  httpOnly: true                                // cookie is not available to JavaScript (client)
}));


router.get('/', function(req, res, next) {
  if (req.session.csrf === undefined) {
    req.session.csrf = randomBytes(100).toString('base64'); // convert random data to a string
  }

  res.render('index', { title: 'Express', token: req.session.csrf });
});

router.post('/', function(req, res, next) {
  if (!req.body.csrf) {
    return res.send(`<p style="font-size: 4rem; color: red;">
                     <strong>CSRF Token not included.</strong>
                     </p>`);
  }

  if (req.body.csrf !== req.session.csrf) {
    return res.send(`<p style="font-size: 4rem; color: red;">
                     <strong>CSRF tokens do not match.</strong>
                     </p>`);
  }

  return res.send(`<p style="font-size: 4rem;">
                   <strong>Successful request!</strong>
                   </p>`);
});
```

```html
extends layout

block content
  h1= title
  p Welcome to #{title}
  form(method='POST' action='/')
    input(type='hidden' name='csrf' value=token)
    label(for="username") Username
    input(type='text' name='username')
    button(type='submit') Submit
```

## Nouveau Projet avec Typescript

### Initialiser l'application

```bash
npm i concurrently nodemon
npm i express liquidjs express-validator cookie-parser cookie-session
npm i -D typescript @types/express @types/node @types/cookie-parser @types/cookie-session
```

```bash
npx tsc --init
```

```json
// tsconfig.json
{
  "compilerOptions": {
    "outDir": "./dist",
  }
}
```

```json
// package.json
{
  "scripts": {
    "build": "npx tsc",
    "start": "node dist/app.js",
    "dev": "concurrently \"npx tsc --watch\" \"nodemon -q dist/app.js\""
  },
}
```

```ts
// app.ts
import express, { Express, Request, Response } from "express";

const app: Express = express()
const port: number = 3000

app.get('/', (req: Request, res: Response): void => {
    res.send("Hello World!")
})

app.listen(port, (): void => {
    console.log(`Server running at http://localhost:${port}`)
})

```

```gitignore
# .gitignore
node_modules
dist # Résultat de la compilation TypeScript vers JavaScript
```

Pour compiler et executer l'application :

```bash
npm run dev # compile et execute l'application
# ou en 2 étapes
npm run build
npm run start
```

### Implémenter le routeur

```ts
// routes/routers.ts
import express, { Router, Request, Response } from 'express'

export const router: Router = express.Router()

router.get('/', (req: Request, res: Response) => {
    res.send("Hello World !")
})
```

```ts
// app.ts
import express, { Express } from "express";
import { router } from "./routes/routes"

const app: Express = express()
const port: number = 3000

app.use('/', router)

app.listen(port, (): void => {
    console.log(`Server running at http://localhost:${port}`)
})
```

### Implémenter un controller

```ts
// controllers/HomeController.ts
import { Request, Response } from "express";

export class HomeController
{
    showHome(req: Request, res: Response)
    {
        res.send("Hello World!")
    }
}

export const homeController = new HomeController()
```

```ts
// routers/home.ts
import { Router } from "express"
import { homeController } from "../controllers/HomeController"

export const home = (router: Router) => {
    router.get('/', homeController.showHome)
}
```

```ts
// routes/routers.ts
import express, { Router, Request, Response } from 'express'
import { home } from './home'

export const router: Router = express.Router()

home(router)
```

### Implémenter une vue (LiquidJS)

```twig
{# view/home/show.html #}
{% layout "layout/index" %}

{% block title %}Hello World{% endblock %}

{% block content %}
<p>Hello World!</p>
{% endblock %}
```

```twig
{# view/layout/index.html #}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{% block title %}{% endblock %}</title>
</head>
<body>
    {% block content %}
    {% endblock %}
</body>
</html>
```

```ts
// middleswares/liquidjs.ts
import { Liquid } from "liquidjs"
import { Express } from "express"
import path from "path"

const viewRootDirectory = path.join(
    __dirname,
    '../',
    'views'
)
const viewFilesExtension = 'html'

export const liquidjs = (app: Express): void => {
    const viewEngine = new Liquid({
        root: viewRootDirectory,
        extname: '.' + viewFilesExtension
    })

    app.engine(viewFilesExtension, viewEngine.express())
    app.set('views', [viewRootDirectory])
    app.set('view engine', viewFilesExtension)
}
```

```ts
// middleswares/middleswares.ts
import { Express } from "express"
import { liquidjs } from "./liquidjs"

export const middleware = (app: Express): void => {
    liquidjs(app)
}
```

```ts
// app.ts
import express, { Express } from "express";
import { router } from "./routes/routes"
import { middleware } from './middlewares/middlewares'

const app: Express = express()
const port: number = 3000

middleware(app)

app.use('/', router)

app.listen(port, (): void => {
    console.log(`Server running at http://localhost:${port}`)
})
```

```ts
// controllers/homeController.ts
import { Request, Response } from "express";

export class HomeController
{
    showHome(req: Request, res: Response): void
    {
        res.render('home/show')
    }
}

export const homeController = new HomeController()
```

### Définir les fichiers statiques (web assets)

```ts
// routes/staticFiles.ts
import path from "path"
import express, { Router, Request, Response } from "express"
import process from "process"

const staticFilesRootPath = path.join(process.cwd(), 'public')

export const staticFiles = (router: Router) => {
    router.use('/public', express.static(staticFilesRootPath))
}

```

```ts
// routes/routes.ts
import express, { Router, Request, Response } from 'express'
import { home } from './home'
import { staticFiles } from './staticFiles'

export const router: Router = express.Router()

home(router)
staticFiles(router)
```

```ts
// public/assets/styles.css
body {
    background-color: rgb(218, 218, 218);
}

```

```html
<!-- /views/layout/index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{% block title %}{% endblock %}</title>
    <link rel="stylesheet" href="public/assets/styles.css">
</head>
<body>
    {% block content %}
    {% endblock %}
</body>
</html>
```

### Ajouter un middleware qui affiche les requêtes dans le log

```ts
// middlewares/logs.ts
import { Express, NextFunction, Request, Response } from "express"

export const logs = (app: Express): void => {
    app.use((req: Request, res: Response, next: NextFunction): void => {
        const httpMethod = req.method
        const urlPath = req.originalUrl

        console.log(`${httpMethod} ${urlPath}`)

        next()
    })
}
```

```ts
// middlewares/middlewares.ts
import { Express } from "express"
import { liquidjs } from "./liquidjs"
import { logs } from "./logs"

export const middleware = (app: Express): void => {
    liquidjs(app)
    logs(app)
}

```

### Chargé la base de donnée Sqlite

```bash
npm i sqlite3
npm i --dev @types/sqlite3
```

```ts
// database/localdb.ts
import { Database } from 'sqlite3'
import path from 'path'
import process from 'process'

const databasePath = path.join(
    process.cwd(),
    "vars",
    "database.db"
)

console.log(databasePath)

export const localdb = new Database(databasePath, (err) => {
    if (err) {
        return console.error(`Error to load database : ${err}`)
    } else {
        console.log('Database loaded.')
        return (err)
    }
})
```

```ts
// database/CommonRepository.ts
import { Database } from "sqlite3";
import { localdb as defaultDatabase } from "./localdb"

export class CommonRepository {
    protected database: Database

    constructor(_database = defaultDatabase)
    {
        this.database = _database
    }

    public getAll(_sql: string, _params: Array<string> = []): Promise<Array<any>>
    {
        return new Promise((resolve, reject) => {
            this.database.all(
                _sql,
                _params,
                (error: any, result: any) => {
                    if (error) {
                        console.log(`Database error : ${error}`)
                        reject(error)
                    } else {
                        resolve(result)
                    }
                }
            )
        })
    }

    public async getOne(_sql: string, _params: Array<string>): Promise<any>
    {
        return new Promise((resolve, reject) => {
            this.database.get(
                _sql,
                _params,
                (error: any, result: any) => {
                    if (error) {
                        console.log(`Database error : ${error}`)
                        reject(error)
                    } else {
                        resolve(result)
                    }
                }
            )
        })
    }

    public async execute(_sql: string, _params: Array<string>): Promise<any>
    {
        return new Promise((resolve, reject) => {
            this.database.run(
                _sql,
                _params,
                (error: any, result: any) => {
                    if (error) {
                        console.log(`Database error : ${error}`)
                        reject(error)
                    } else {
                        resolve(result)
                    }
                }
            )
        })
    }
}

export const commonRepository = new CommonRepository()

```

```ts
// controllers/HomeController.ts
import { Request, Response } from "express";
import { baseRepository } from "../database/BaseRepository";

export class HomeController
{
    async showHome(req: Request, res: Response): Promise<void>
    {
        let testDatabase = await baseRepository.getAll("SELECT * FROM users")

        res.render('home/show')
    }
}

export const homeController = new HomeController()

```

### Implémenté une entité

```ts
// database/User.ts
export class User
{
    private _id: number|null
    private _name: string
    private _password: string
    private _quote: string

    constructor(
        name: string,
        password: string,
        quote: string,
        id?: number
    ) {
        this._name = name
        this._password = password
        this._quote = quote
        this._id = id || null
    }

    public set id(id: number|null)
    {
        this._id = id
    }

    public get id(): number|null
    {
        return this._id
    }

    public set password(password: string)
    {
        this.password = password
    }

    public get password(): string
    {
        return this._password
    }

    public set name(name: string)
    {
        this._name = name
    }

    public get name(): string
    {
        return this._name
    }

    public set quote(quote: string)
    {
        this._quote = quote
    }

    public get quote(): string
    {
        return this._quote
    }
}

```

```ts
// database/BaseRepository.ts
import { commonRepository, CommonRepository } from "./CommonRepository";

export abstract class BaseRepository {
    protected table: string
    protected repository: CommonRepository

    constructor(
        _table: string,
        _commonRepository: CommonRepository = commonRepository
    )
    {
        this.table = _table
        this.repository = _commonRepository
    }
}
```

```ts
// database/UserRepository.ts
import { BaseRepository } from "./BaseRepository";
import { User } from "./User"

export class UserRepository extends BaseRepository
{
    constructor()
    {
        super("users")
    }

    public async getAll(): Promise<Array<User>|null>
    {
        try {
            let arrayUsers: Array<User> = []
            let arrayRawResult = await this.repository.getAll(
                `SELECT id, name, password, quote FROM ${this.table}`
            )

            if (arrayRawResult === undefined) {
                return null
            }

            arrayRawResult.forEach((userRaw) => {
                arrayUsers.push(new User(
                    userRaw.name,
                    userRaw.password,
                    userRaw.quote,
                    userRaw.id
                ))
            })

            return arrayUsers
        } catch (error) {
            console.error(`Error to retrieve all users : ${error}`)
            return null
        }
    }

    public async getById(id: number): Promise<User|null>
    {
        try {
            let rawResult = await this.repository.getOne(
                `SELECT id, name, password, quote FROM ${this.table} WHERE id=?`,
                [String(id)]
            )
    
            if (rawResult === undefined) {
                return null
            }
    
            return new User(
                rawResult.name,
                rawResult.password,
                rawResult.quote,
                rawResult.id
            )
        } catch (error) {
            console.error(`Error to retrieve an user with ID ${id} : ${error}`)
            return null
        }
    }

    public async add(user: User): Promise<void>
    {
        try {
            this.repository.execute(
                `INSERT INTO ${this.table} (name, password, quote) VALUES (?, ?, ?)`,
                [user.name, user.password, user.quote]
            )
        } catch (error) {
            console.error(`Error to add an user (id : ${user.id}): ${error}`)
        }
    }

    public async update(id: number, user: User): Promise<boolean>
    {
        try {
            let currentUser = await this.getById(id)

            if (!currentUser) {
                return false
            }

            this.repository.execute(
                `UPDATE ${this.table} SET name=?, password=?, quote=? WHERE id=?`,
                [user.name, user.password, user.quote, String(id)]
            )

            return true
        } catch (error) {
            console.error(`Error to update an user (id : ${id}): ${error}`)
            return false
        }
    }

    public async deleteById(id: number): Promise<boolean>
    {
        try {
            let currentUser = await this.getById(id)

            if (!currentUser) {
                return false
            }

            this.repository.execute(
                `DELETE FROM ${this.table} WHERE id=?`,
                [String(id)]
            )
            return true
        } catch (error) {
            console.error(`Error to remove user with id ${id}: ${error}`)
            return false
        }
    }
}

export const userRepository = new UserRepository()

```

```ts
// controllers/HomeController.ts
import { Request, Response } from "express";
import { userRepository } from "../database/UserRepository";

export class HomeController
{
    async showHome(req: Request, res: Response): Promise<void>
    {
        let allUsers = await userRepository.getAll()
        console.log(allUsers)
        res.render('home/show')
    }
}

export const homeController = new HomeController()

```

### Formulaire et entrées pour les utilisateurs

Gérer la récupération des données avec la methode POST :

```ts
// middlewares/bodyParser.ts
import express, { Express } from 'express'

export const bodyParser = (app: Express): void => {
    app.use(express.urlencoded({extended: true}))
}
```

```ts
// middlewares/middlewares.ts
import { Express } from "express"
import { bodyParser } from "./bodyParser"
import { liquidjs } from "./liquidjs"
import { logs } from "./logs"

export const middleware = (app: Express): void => {
    liquidjs(app)
    logs(app)
    bodyParser(app)
}
```

Ajouter le controlleur qui va récupérer les données :

```ts
// controllers/UserController.ts
import { Request, Response } from "express";
import { validationResult } from "express-validator";
import { userRoutesURL } from "../routes/user";

export class UserController
{
    showAll(req: Request, res: Response): void
    {
        res.render('user/showAll')
    }

    showAddUserForm(req: Request, res: Response): void
    {
        res.render(
            'user/add',
            {
                form_destination: userRoutesURL.add,
                form_send_method: "post"
            }
        )
    }

    addUser(req: Request, res: Response)
    {
        const { name, password, quote } = req.body
        const validationErrors = validationResult(req)

        if (!validationErrors.isEmpty()) {
            res.render(
                'user/add',
                {
                    form_destination: userRoutesURL.add,
                    form_send_method: "post",
                    form_errors: validationErrors.mapped(),
                    user: {
                        name: name,
                        password: password,
                        quote: quote
                    }
                }
            )
        } else {
            res
                .send(`L'utilisateur ${name} a bien été créer.`)
                .status(200)
                .end()
            //res.redirect(userRoutesURL.showAll)
        }
    }
}

export const userController = new UserController()
```

Gérer le validateur d'entrée de l'utilisateur :

```ts
// form/userValidator.ts
import { checkSchema } from "express-validator";
import { Schema } from "express-validator/src/middlewares/schema";
import { AlphaLocale } from "express-validator/src/options";

const localeFrench: AlphaLocale = "fr-FR"

const userSchema: Schema = {
    name: {
        trim: true,
        escape: true,
        notEmpty: {
            options: {
                ignore_whitespace: true
            },
            errorMessage: "Le nom est requis"
        },
        isAlpha: {
            options: [
                localeFrench,
                {
                    ignore: ' -'
                }
            ],
            errorMessage: "Le nom ne doit contenir que des caractères alphabétiques, des espaces des tirets '-'"
        },
        isLength: {
            options: {
                min: 2,
                max: 32
            },
            errorMessage: "Le nom doit contenir entre 2 et 32 caractères"
        }
    },
    password: {
        escape: true,
        notEmpty: {
            options: {
                ignore_whitespace: true
            },
            errorMessage: "Le mot de passe est requis"
        },
        isStrongPassword: {
            options: {
                minLength: 8,
                minLowercase: 1,
                minUppercase: 1,
                minSymbols: 1,
                minNumbers: 1
            },
            errorMessage: "Le mot de passe doit avoir une taille minimal de 8, avoir au moin une majuscule, une minuscule, un caractère spécial et un chiffre"
        },
        isLength: {
            options: {
                min: 8,
                max: 64
            },
            errorMessage: "Le mot de passe doit contenir entre 8 et 64 caractères"
        }
    },
    quote: {
        trim: true,
        escape: true,
        notEmpty: {
            options: {
                ignore_whitespace: true
            },
            errorMessage: "La citation est requis"
        },
        isAlpha: {
            options: [
                localeFrench,
                {
                ignore: ` -,.!?:\'`
            }],
            errorMessage: "La citation ne doit contenir que des caractères alphabétiques, des espaces et les caractères: '-,.!?:'"
        },
        isLength: {
            options: {
                min: 2,
                max: 32
            },
            errorMessage: "Le nom doit contenir entre 2 et 32 caractères"
        }
    }
}

const userIdSchema: Schema = {
    id: {
        trim: true,
        escape: true,
        toInt: true,
        isInt: {
            errorMessage: "L'ID de l'utilisateur doit être un nombre"
        },
        notEmpty: {
            options: {
                ignore_whitespace: true
            },
            errorMessage: "L'ID de l'utilisateur doit être défini"
        }
    }
}

export const userValidator = checkSchema(userSchema)
export const userIdValidator = checkSchema(userIdSchema)
```

Ajout des chemins et activation de la vérification :

```ts
// routes/user.ts
import { Router } from "express";
import { userController } from "../controllers/UserController";
import { userValidator } from "../form/userValidator";

export const userRoutesURL = {
    showAll: "/user/",
    add: "/user/add"
}

export const user = (router: Router) => {
    router.get(userRoutesURL.showAll, userController.showAll)
    router.get(userRoutesURL.add, userController.showAddUserForm)
    router.post(userRoutesURL.add, userValidator, userController.addUser)
}
```

```ts
// routes/routes.ts
import express, { Router, Request, Response } from 'express'
import { home } from './home'
import { user } from './user'
import { staticFiles } from './staticFiles'

export const router: Router = express.Router()

home(router)
user(router)

staticFiles(router)
```

Les vues :

```html
<!-- view/user/showAll.html -->
{% layout "layout/index" %}

{% block title %}Afficher les utilisateurs{% endblock %}

{% block content %}
<h1>Liste de tous les utilisateurs</h1>

<ul>
    <li>Toto</li>
    <li>Tata</li>
    <li>Titi</li>
</ul>
{% endblock %}
```

```html
<!-- views/user/add.html -->
{% layout "layout/index" %}

{% block title %}Ajouter un utilisateur{% endblock %}

{% block content %}
<h1>Ajouter un utilisateur</h1>

{% 
    render "./form/user.html",
    action: form_destination,
    method: form_send_method,
    errors: form_errors,
    user: user,
    submit_button_content: "sauvegarder"
%}

{% endblock %}
```

```html
<!-- views/user/form/user.html -->
<form action="{{ action }}" method="{{ method }}">
    <label for="name">Nom :
        <input
            type="text"
            id="name"
            name="name"
            value="{{ user.name }}"
            placeholder="Nom de l'utilisateur"
            required
        >
        <p>{{ errors.name.msg }}</p>
    </label>

    <label for="password">Mot de passe :
        <input
            type="password"
            id="password"
            name="password"
            value="{{ user.password }}"
            placeholder="Mot de passe de l'utilisateur"
            required
        >
        <p>{{ errors.password.msg }}</p>
    </label>

    <label for="quote">Citation :
        <input
            type="text"
            id="quote"
            name="quote"
            value="{{ user.quote }}"
            placeholder="Citation de l'utilisateur"
            required
        >
        <p>{{ errors.quote.msg }}</p>
    </label>

    <div>
        <button type="submit">
            {{ submit_button_content }}
        </button>
    </div>
</form>
```

### Vérifier les entrée avec les token CSRF

```ts
// services/TokenCsrf.Ts
import { Request } from "express";
import { randomBytes } from "crypto";
import CookieSessionObject from "cookie-session";
import { Session } from "inspector";

export class TokenCsrf
{
    private currentSession: any

    constructor(req: Request)
    {
        if (req.session) {
            this.currentSession = req.session
            this.generateTokenIfNotExist()
        } else {
            throw new Error("There is no session available!")
        }
    }

    public getToken(): string
    {
        return this.currentSession.tokenCsrf
    }

    public isEqual(userToken: string)
    {
        return this.currentSession.tokenCsrf === userToken
    }

    private generateTokenIfNotExist()
    {
        if (this.currentSession.tokenCsrf === undefined) {
            this.generateToken()
        }
    }

    private generateToken(): void
    {
        this.currentSession.tokenCsrf = randomBytes(100).toString('base64')
    }
}
```

```ts
// controllers/UserController.ts
import { Request, Response } from "express";
import { validationResult } from "express-validator";
import { userRoutesURL } from "../routes/user";
import { TokenCsrf } from "../services/TokenCsrf"

export class UserController
{
    showAll(req: Request, res: Response): void
    {
        res.render('user/showAll')
    }

    showAddUserForm(req: Request, res: Response): void
    {
        const serverTokenCsrf = new TokenCsrf(req)

        res.render(
            'user/add',
            {
                form_destination: userRoutesURL.add,
                form_send_method: "post",
                tokenCsrf: serverTokenCsrf.getToken()
            }
        )
    }

    addUser(req: Request, res: Response)
    {
        const { name, password, quote, tokenCsrf } = req.body
        const validationErrors = validationResult(req)
        const serverTokenCsrf = new TokenCsrf(req)

        if (!serverTokenCsrf.isEqual(tokenCsrf)) {
            res.render(
                'user/add',
                {
                    form_destination: userRoutesURL.add,
                    form_send_method: "post",
                    tokenCsrf: serverTokenCsrf.getToken()
                }
            )
        } else if (!validationErrors.isEmpty()) {
            res.render(
                'user/add',
                {
                    form_destination: userRoutesURL.add,
                    form_send_method: "post",
                    form_errors: validationErrors.mapped(),
                    tokenCsrf: serverTokenCsrf.getToken(),
                    user: {
                        name: name,
                        password: password,
                        quote: quote
                    }
                }
            )
        } else {
            res
                .send(`L'utilisateur ${name} a bien été créer.`)
                .status(200)
                .end()
            //res.redirect(userRoutesURL.showAll)
        }
    }
}

export const userController = new UserController()
```

```html
<!-- views/user/add.html -->
{% layout "layout/index" %}

{% block title %}Ajouter un utilisateur{% endblock %}

{% block content %}
<h1>Ajouter un utilisateur</h1>

{% 
    render "./form/user.html",
    action: form_destination,
    method: form_send_method,
    errors: form_errors,
    user: user,
    tokenCsrf: tokenCsrf,
    submit_button_content: "sauvegarder"
%}

{% endblock %}
```

```html
<!-- views/user/form/user.html -->
<form action="{{ action }}" method="{{ method }}">
    <label for="name">Nom :
        <input
            type="text"
            id="name"
            name="name"
            value="{{ user.name }}"
            placeholder="Nom de l'utilisateur"
            required
        >
        <p>{{ errors.name.msg }}</p>
    </label>

    <label for="password">Mot de passe :
        <input
            type="password"
            id="password"
            name="password"
            value="{{ user.password }}"
            placeholder="Mot de passe de l'utilisateur"
            required
        >
        <p>{{ errors.password.msg }}</p>
    </label>

    <label for="quote">Citation :
        <input
            type="text"
            id="quote"
            name="quote"
            value="{{ user.quote }}"
            placeholder="Citation de l'utilisateur"
            required
        >
        <p>{{ errors.quote.msg }}</p>
    </label>

    <input
        type="hidden"
        name="tokenCsrf"
        value="{{ tokenCsrf }}"
    >

    <div>
        <button type="submit">
            {{ submit_button_content }}
        </button>
    </div>
</form>

```
