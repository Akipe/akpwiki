---
title: TypeScript
description: 
published: true
date: 2024-05-21T14:42:58.767Z
tags: 
editor: markdown
dateCreated: 2024-05-21T14:39:51.201Z
---

# TypeScript

Typescript est un transcriver JS pour ajouter des fonctionnalités en JS comme le typage.

- <https://www.codeheroes.fr/2023/05/05/typescript-programmation-de-types/>

## Installation

### Local

Installation dans le projet (local) :
```bash
npm install --save-dev typescript
# La même commande avec des raccourcies
npm i -D typescript
```

Dans le projet, il faudra ajouter avant chaque commande TypeScript `npx` :

```bash
npx tsc index.ts
```
Ou :
```bash
./node_modules/typescript/bin/tsc index.ts
```

### Global

Non recommandé.

Pour une installation accessible à travers l'ensemble de l'espace utilisateur (global) :
```bash
npm i -g typescript
```

On peut ensuite utiliser la commande `tsc` n'importe où.

## Configuration

Pour générer le fichier de configuration `tsconfig.json` :

```bash
npx tsc --init
```

Références pour l'ensemble des paramètres disponibles pour `tsconfig.json` : <https://www.typescriptlang.org/tsconfig>

Configurations recommandés : <https://github.com/tsconfig/bases/>

### Configuration pour JS navigateur

```json
/* tsconfig.json */
{
  "compilerOptions": {
    "target": "es2016",
    "module": "es2015",
    "moduleResolution": "node",
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "strict": true,
    "skipLibCheck": true
  }
}
```

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TypeScript for the web</title>
</head>
<body>
    <script type="module" src="./index.js"></script> <!-- utiliser le paramètre type="module" -->
</body>
</html>

```

```typescript
// index.ts
import { data } from './data.js';

alert(data.message);
```

```typescript
// data.ts
export const data = {
    message: 'Hello world!',
}
```

Il faut utiliser un serveur web local pour développer, à cause de la sécurité des navigateurs internet (CORS policy: Cross origin requests).

### Configuration pour NodeJS

```json
/* tsconfig.json */
{
  "compilerOptions": {
    "target": "es2022",
    "module": "commonjs",
    "moduleResolution": "node",
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "strict": true,
    "skipLibCheck": true,
  }
}
```

```typescript
// app.ts
console.log("Hello World!");
```

### Configurations utiles

| Paramètre | Description | valeurs possibles | Notes
|---|---|---|---
| `rootDir` | Chemin des fichiers sources TypeScript | `"src"`
| `outDir` | Chemin des fichiers JS compilé depuis le TypeScript | `"dist"`
| `baseUrl` |  | `""`
| `sourceMap` | Pouvoir plus facilement débugger avec les sources map | `true` ou `false`

## Commandes

### Compilation

Pour compiler le TypeScript :

```bash
npx tsc
```

Pour compiler après chaque modification du fichier en temps réelle :

```bash
npx tsc --watch
```

## Différences avec le JS

### Typage

#### Variables simples

```js
// JS
let a
let b = 3
b = "une chaine de caractère" // Pas d'erreurs
```
```ts
// TS
let a: number
// ou typage implicite
let b = 3
b = "une chaine de caractère" // Type 'string' is not assignable to type 'number'
```

### Tableaux

```js
// JS
let anArrayOfString
anArrayOfString = ['Hello', 'World!']
// ou
let anArrayOfString = ['Hello', 'World!'
anArrayOfString.push(1337) // Pas d'erreurs
```
```ts
// TS
let anArrayOfString: string[]
// ou
let anArrayOfString: Array<string>
anArrayOfString = ['Hello', 'World!']
// ou 
let anArrayOfString: string[] = ['Hello', 'World!']
let anArrayOfString: Array<string> = ['Hello', 'World!']
anArrayOfString.push(1337) // Erreur
```

On peut également créer des Tuples, qui peuvent avoir différents types :

```ts
// TS
let aTuple: [string, number]
aTuple = ["Hello", 42]
```

#### Fonctions

```js
// JS
function demo(_selector, _options)
{
  console.log(`${_options.ease}: ${options.duration}`)
  return document.querySelector(_selector)
}

let demo = (_selector) => { document.querySelector(_selector) }
```

```ts
// TS
function demo(_selector: string, options: {ease: string, duration: number}): Element
{
  console.log(`${_options.ease}: ${options.duration}`)
  return document.querySelector(_selector)
}
// Une fonction qui retourne plusieurs types de valeurs
function demo(_selector: string): Element | undefined
{
  return document.querySelector(_selector)
}

let demo = (_selector: string): Element | undefined => { document.querySelector(_selector) }
```

#### Objets

```js
// JS
let unObjet = { message: "Hello World!", words: 2}
```

```ts
// TS
let unObjet: { message: string, numberWords: number } = { message: "Hello World!", words: 2}
```

#### Liste des typages

Par défaut, tous les types acceptent, en plus de leur typage, les types `null` et `undefined`. Pour changer celà, il faut actier le "strict null check" (voir ci-dessous).

- `string`
- `number`
- `boolean`
- `void`
- `Object`
- `unknown` : pour accepter tous les types possibles, on ne peut tester avec `typeof`
- `any` : similaire au fonctionnement classique du JS, comme la possibilité d'accéder à des propriétés non existantes.
- `null`
- `undefined`

#### Activer le "Strict Null Checks"

Si vous souhaiter activer la vérification forte des typages pour empécher l'attribution des valeurs `null` et `undefined` aux autres typages, il vous faut l'activer dans le fichier de configuration de TS :

```json
{
  "compilerOptions": {
    "strictNullChecks": true
  }
}
```

#### Attribution de typage depuis des éléments existants

On peut également attribuer des typages depuis des éléments existants, avec `typeof` et `ReturnType<T>` :

```ts
// TS
function getDog(name: string): Dog
{
  return // ... On retourne un objet Dog
}

// On créer un type depuis la fonction existante
type getDogType = typeof getDog // (name: string) => Dog

// On peut également créer un type depuis le retour d'une fonction
type sameAsTheReturnOfFunction = ReturnType<getDog> // Dog
```

#### Création de ses propres types

```ts
// TS
type Dog = {
  name: string,
  age: number,
  cute: boolean
}
let aExampleDog: Dog = { name: 'Idefix', age: 2, cute: true }

// Les interfaces sont égalements très utilisés pour créer de nouveaux types
interface Dog {
  name: string,
  age: number,
  cute: boolean
}
let aExampleDog: Dog = { name: 'Idefix', age: 2, cute: true }

```

#### Generics

Les Generics permettent de créer des typages qui peuvent varier lors de la création de l'élément.  
On peut les nommer avec n'importe quelle lettre.

```ts
// TS
// "T" est un Generic
interface Dog<T>
{
  name: string,
  someInformation: T
  cute: boolean
}
let firstDog: Dog<number> = { name: "Idefix", someInformation: 42, cute: true }
let secondDog: Dog<string> = { name: "Tartiflette", someInformation: "miam", cute: false }

// On peut en définir plusieurs
interface Dog<N, I, C>
{
  name: N,
  someInformation: I
  cute: C
}

// On peut les utiliser également dans les fonctions
function getDog<N, I, C>(_name: N): Dog<N, I, C>
{
  // ...
}
```

### Class

```typescript
// TS
export class User
{
    private _id: number
    private _name: string
    private _password: string

    constructor(
        id: number,
        name: string,
        password: string,
        quote: string
    ) {
        this._id = id
        this._name = name
        this._password = password
    }

    public set id(id: number)
    {
        this._id = id
    }

    public get id(): number
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
}
```

Heritage

```ts
// Base class
class Person {
  Name: string;
  constructor(name: string) {
    this.Name = name;
  }
}
// Deriving Teacher class
class Teacher extends Person {
  Payment: number;
  constructor(name: string, payment: number) {
    super(name);
    this.Payment = payment;
  }
  display(): void {
    console.log("Teacher's Name: " + this.Name);
    console.log("Teacher's Payment " + this.Payment);
  }
}
// Create Object
let obj = new Teacher("GeeksforGeeks", 8500000);
obj.display();
```

Classes abstraites

```ts
abstract class Person {
    name: string;
    
    constructor(name: string) {
        this.name = name;
    }

    display(): void{
        console.log(this.name);
    }

    abstract find(string): Person;
}

```

### Interfaces

On utilise souvent les interfaces pour définir des typages (voir les types ci dessus).

```ts
// TS
interface Dog {
  cute: boolean // propriétée
  give_food: () => void // fonction
  give_bath: (use_shampoo: boolean) => void // fonction
  get_name: () => string // fonction
}
```

### Enumérations

```ts
// TS
enum Color { // Par défaut, la valeur commencera à 0
  Red,
  Green,
  Blue,
}

let aRandomColor: Color = Color.Green

enum Color {
  Red = 10, 
  Green, // = 11
  Blue, // = 12
}

enum Color {
  Red = 4, 
  Green = 2,
  Blue = 42,
}

// On peut récupérer le nom de la valeur de l'énumération
let colorName: string = Color[42] // On récupére le nom de la couleur ayant la valeur 42
console.log(colorName) // "Blue"
```

### Namespaces

```ts
// TS
namespace MonApp {
  export let maVarAccessible = 1
  let uneAutreNonAccessible = 4
  export class Demo{}
}

MonApp.maVarAccessible // 1
MonApp.uneAutreNonAccessible // Erreur
let exemple = new MonApp.Demo() // Objet de type MonApp.Demo
```

### Modules

```ts
// TS
// demo.ts
export let uneVariable = 3
export class Demo{}
```

```ts
// TS
// index.ts
import { uneVariable, Demo } from './demo'
uneVariable // 3
let testDemo = new Demo()
```

## Utilisation avec des bibliothèques JS

### Générale

Vous pouvez utiliser TypeScript avec des bibliothèques JS, mais vous n'aurez pas l'aide de TS.  
Par contre, vous pouver "surcharger" ces bibliothèques avec des modules `@types` créer par vous même ou par la communauté qui va proposer un typage fort à ces bibliothèques.  
Ce sont des fichiers `.d.ts`.

Pour rechercher des typages TS dans NPM, il faut rajouter `@types\` devant le nom du paquet NPM :

```bash
# Pour le typage TS de node :
npm install --dev @types/node

# Pour le typage TS d'express :
npm install --dev @types/express
```

Liste de typages créer par la communauté pour des bibliothèques JS : [https://github.com/DefinitelyTyped/DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped)

### Express

```bash
npm i -D typescript @types/express @types/node
npm i -D concurrently nodemon
```

```bash
npx tsc --init # Générer le fichier de config tsconfig.json
```

Ajouter la destination de la compilation de typescript :

```json
// tsconfig.json
{
  "compilerOptions": {
    "outDir": "/dist"
    // le reste des options
  }
}
```

```json
//package.json
{
  "scripts": {
    "build": "npx tsc",
    "start": "node dist/index.js",
    "dev": "concurrently \"npx tsc --watch\" \"nodemon -q dist/index.js\""
  }
}
```

Voici un exemple ensuite de conversion du fichier index.js qui initialise un projet ExpressJS :

```js
/* JavaScript */

const express = require('express')

const app = express()
const port = 3000

app.get('/', (req, res) => {
    res.send('Express + TS')
})

app.listen(port, () => {
    console.log(`[server]: Server is running at https://localhost:${port}`)
})
```

```ts
/* TypeScript */

import express, { Express, Request, Response } from 'express';

const app: Express = express()
const port: number = 3000

app.get('/', (req: Request, res: Response): void => {
    res.send('Express + TS')
})

app.listen(port, (): void => {
    console.log(`[server]: Server is running at https://localhost:${port}`)
})
```

- https://www.codemag.com/Article/2011021/A-Simple-ExpressJS-and-TypeScript-Project
- https://www.digitalocean.com/community/tutorials/setting-up-a-node-project-with-typescript
- https://www.toptal.com/express-js/nodejs-typescript-rest-api-pt-1
- https://blog.logrocket.com/how-to-set-up-node-typescript-express/